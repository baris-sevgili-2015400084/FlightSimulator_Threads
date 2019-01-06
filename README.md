# FlightSimulator_Threads
A Flight Simulator Program, written in a parallel programming manner, language: C

In this project we were asked to implement a program in which we exercise thread concept and
handling critical sections mainly. The musts of the project were implementing the code in
multi-threading fashion, not doing it a sequentially working code, not taking all the section as
critical section, creating the server as soon as client arrives.

In my code I used an isAvailable array to detect the seats that can be picked for
reservation, which are not reserved yet. In order to passing variables that both I want to achieve
from inner parts, from clients and from servers; I used a struct structure which has the id of the
client of the related struct and the seat number, that related client picked for reservation.
Actually I passed pointers which points to that struct.

In Client thread, I create the server for that client as soon as possible, after client sleeps
for a while. I also passed the pointer of the struct to the server when creating it. Picking a
random seat, checking the availability of that seat made in the client thread, accordingly I used
a mutex which encapsulates the scope where I reach my shared data, in order to prevent any
other thread to manipulate its value, when current thread is using it, and unlocked it after the
thread’s job is done. After creating the server thread, server thread continuously checks whether
the client found any available seat in order to reserve (busy-waiting). As soon as client find
one, server prints that client has reserved related seat.


 To compile my program: (Also there is Makefile attached, to compile easier)
gcc my_project.c -o my_executable -lpthread

To run the program, having “number_of_seats” clients and seats:
./my_executable number_of_seats
