# Project Workshop Meeting

## Meeting Start Time

2025/02/13/15:00

## Meeting End Time

2025/02/13/15:30

## Location/Medium

Meeting was held over Discord after class, due to Riley being in a separate class section.

## Present

Levi, Riley, Tia 

## Minute Recorder

Levi

## Things clarified

We used this time to discuss the feedback that we got from the iteration 3 meetings. One thing was very clear - our main testing
framework was heavily lacking. Our endpoints were bloated and doing too much, and the tests did not properly test the endpoints like
they should have. This was a very large part of the feedback, and what we believe was the most important thing missing
from iteration 3.

## Progress Made

We used this time to work on the testing. Mainly, we made a class fixture for our database, and began moving some functions
from the endpoints into their own files. We have individual classes that hold these functions now, including a class that handles the
audit services. Through Xunit and the class fixture, we were able to make a properly working class that didn't need to go through an endpoint
to recieve the proper result, and can check the test database directly to ensure the right result was met.