Download Link: https://assignmentchef.com/product/solved-simulation-of-a-bank
<br>
5/5 - (1 vote)

Implement the event-driven simulation of a bank. A queue of arrival events will represent the line of customers in the bank. Maintain the arrival events and departure events in a priority queue, sorted by the time of the event. Use a link-based implementation for the event list. The input is a text ﬁ le of arrival and transaction times. Each line of the ﬁ le contains the arrival time and required transaction time for a customer. The arrival times are ordered by increasing time. Your program must count customers and keep track of their cumulative waiting time. These statistics are sufﬁ cient to compute the average waiting time after the last event has been processed. Display a trace of the events executed and a summary of the computed statistics (the total number of arrivals and average time spent waiting in line).



EXTRA CREDIT:  You can get up to a 25/20 by completing 7C.  Even though this is extra credit, you should at least look at it (as you are likely to see it again very soon)

For this assignment you may (and probably should) use the C++ STL queue and priority_queue.  A priority queue is similar in concept to a queue, but the priority queue takes care of sorting every entry AS IT IS entered in the queue.  So when you pop from the front, it always takes the highest value off the queue.

_________________________________

So at a very high level.  You are creating a priority queue that has the events.  You can have arrival and departure events (Think one variable that lists either arrival or departure).  This is sorted by the time of arrival or departure (respectively).  Because it is a priority queue, every add or delete action forces the built-in functions of the priority queue to sort it on the time of arrival.  As a result you have a mix of arrival and departure events mixed in with each other.  Priority queues normally sort by the highest (time) but we want it to sort on lowest, so you can subtract the time from a very large number.  10000-1 = 9999 (making it a high priority).  10000-9999 = 1 (making it a low priority) .

If it is an arrival type of event at the top of the priority queue:  Get the value of the top item, then pop it off.   If there are no people in the bankline (queue)  and the teller is available then process that event.  In processing the event, we add a departure event to the priority queue (and it will sort itself), starting at the current time plus the listed transaction time (teller is unavailable for more customers during that transaction.  In that departure even we keep track of the original arrival time.

If it is a departure event at the top of the priority queue:  Get the value of the top item then pop it off and process the departure.   If there are no people in the bankline (queue).  Because someone just finished with the teller, the teller is now available for another customer.  Look in the bankline (queue) to see if there are any people in the bankline.

When you have a departure event, you have enough information to determine how much the customer waited.

——-

This is how the book determines the wait time.  Note that A has no wait time.  Taken care of on arrival at 1.  Then B arrived at 2 and was seen at 6….so waited for 4.  Then C arrived at 4, but wasn’t seen until 11, making a wait of 7.  C finishes at 16, but D doesn’t arrive until 20…so no wait.  Then there are waits until J.  I ends at 50 and J doesn’t get there until 88, so is seen right away.  The total wait time is 56 with 10 arrivals, so 5.6

Arrival#StartEndWaitA160B2114C4167D20250E22303F24356G26409H284512I305015J88910