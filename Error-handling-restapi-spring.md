# Error Handling for REST with Spring

# Overview
Spring 3.2 trở về **trước**, có 2 cách chính để handle exception trong Spring MVC là:
* *HandlerExceptionResolver*
* *@ExceptionHandler* annotation.

Bắt đầu từ **3.2**, Spring sử dụng *@ControllerAdvice* annotation để giải quyết 2 giới hạn của những 2 solution trên.


# Solution 1 - *@ExceptionHandler*
The first solution work at the **Controller level** .

For example:

    public class FooController {
	    @ExceptionHandler({CustomExc1.class, CustomExc2.class})
	    public void handleException() {
		    .........
	    }
    }

We'll define a method to handle exceptions and annotate that with *@ExceptionHandler* which is only action for that particular Controller.

=> This approach is the major drawback.

# Solution 2 - The HandlerExceptionResolver
This solution will resolve any exception thrown by the app and allow us to implement a **uniform exception handling mechanism** in REST API

## ExceptionHandlerExceptionResolver
This is enabled by default in the DispatcherServlet. This is actually the core component of how the *@ExceptionHandler* mechanism presented earlier works. 
## DefaultHandlerExceptionResolver
Enabled by default in the DispatcherServlet.

This resolve standard Spring exception to their corresponding HTTP Status code (Client error - 4xx and Server error - 5xx).

This **only set the HTTP Status Code** of the Response properly, but it **doesn't set anything to body** of response.

## ResponseStatusExceptionResolver
Enabled by default in the DispatcherSerlvet. 
Its main responsibility is to use the *@ResponseStatus* annotation **available on custom exceptions** and to map these exceptions to HTTP Status Code .

For example:

    @ResponseStatus(value = HttpStatus.NOT_FOUND)
    public class CustomExc extends RuntimeException {
	    public CustomExc() {
		    super();
	    }
	    public CustomExc(String msg) {
		    super(msg);
	    }
	    public CustomExc(String msg, Throwable cause) {
		    super(msg, cause);
	    }
	    .....blabla
    }

But, It like the above exceptions, which is limited in the way it deals with the body of response.
* Deal with: solve a problem or make a decision, or give your attention to s.one/s.thing.

## SimpleMappingExceptionResolver and AnnotationMethodHandlerExceptionResolver


## HandlerExceptionResolver


# New Solution 3 - @ControllerAdvice annotation

**Spring 3.2** brings support for a  global *@ExceptionHandler* with the new *@ControllerAdvice* annotation. This enable the mechanism that **makes use of *ResponseEntity*** along with type safety and flexibility of *@ExceptionHandler*.

> Multiple *@ExceptionHandler* to **single, global* error handling component.

    @ControllerAdvice
    public class RestExceptionHandler extends ResponseEntityExceptionHandler {
	    @ExceptionHandler({
		    IllegalArgumentException.class,
		    IllegalStateException.class})
	    protected ResponseEntity<Object> handleConflict (RuntimeException exc, WebRequest req) {
		    String bodyOfResponse = "....bla..bla";
		    return handleExceptionInternal(
				    ex, 
					bodyOfResponse, 
					new HttpRequest(),
					HttpStatus.Conflict, 
					req);
    }
    }

Not only simple but also flexible:

 - Allow full control the body of response .
 - Allow mapping of several exceptions to the same method (to be handled together).
 - Allow makes use of ResponseEntity in REST API

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzIwNzQyNTIyLDc3MDc4NzQ0NiwxMDE2Nj
UzMjMwLC03MjExNTA5NzQsMTQyNTA3OTMxMSwtMTA4MDQ0MzI4
OSwyNTA4MzY2OTYsOTIxMzcyNTUwLC0xOTM1MjQ2MzM0XX0=
-->