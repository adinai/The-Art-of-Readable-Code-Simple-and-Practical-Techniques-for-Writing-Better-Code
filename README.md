#### Notes from The-Art-of-Readable-Code

Part One - Surface Level Improvemnts
======
###### Packing Information into the names. <h6> 
1. **Use specific words**—for example, instead of Get, words like Fetch or Download might be better, depending on the context. 
2. **Avoid generic names** like tmp and retval, unless there’s a specific reason to use them.
3. **Use concrete names** that describe things in more detail—the name ServerCanStart() is vague compared to CanListenOnPort(). 
4. **Attach important details** to variable names—for example, append _ms to a variable whose value is in milliseconds or prepend raw_ to an unprocessed variable that needs escaping. 
5. **Use longer names for larger scopes**—don’t use cryptic one- or two-letter names for variables that span multiple screens; shorter names are better for variables that span only a few lines.
6. **Use capitalization, underscores, and so on in a meaningful way**—for example, you can append “_” to class members to distinguish them from local variables.

# Names that Cant be Misconstrued. <h1> tag page 31
# Aesthetics. <h1> tag page 43





## This is an <h2> tag


Packing Information into the names.

The single theme for this chapter is: pack information into your names. By this, we mean that the reader can extract a lot of information just from reading the name.
Here are some specific tips we covered:
• Use specific words—for example, instead of Get, words like Fetch or Download might be better, depending on the context. 
• Avoid generic names like tmp and retval, unless there’s a specific reason to use them.
PACKING INFORMATION INTO NAMES 21
• Use concrete names that describe things in more detail—the name ServerCanStart() is vague compared to CanListenOnPort(). 
• Attach important details to variable names—for example, append _ms to a variable whose value is in milliseconds or prepend raw_ to an unprocessed variable that needs escaping. 
• Use longer names for larger scopes—don’t use cryptic one- or two-letter names for variables that span multiple screens; shorter names are better for variables that span only a few lines.
• Use capitalization, underscores, and so on in a meaningful way—for example, you can append “_” to class members to distinguish them from local variables.


Advices: 

	- The clearest way to name a limit is to put max_ or min_ in front of the thing being limited.
  
  Simplifying loops and logic
Way to refine the loops, logic, and variables in your program to make easier to understand

Reorganizing your code
Higher-level ways to organize large blocks of code and attack problems at the function level.

Selected topics
Applying "easy to understand" to testing and to a large data structure coding

So even though having fewer lines of code is a good goal, minimizing the time-till understanding is an even better goal.

Craetive Way of Simplifying Expressions

```javascript

var update_highlight = function (message_num) {    
if ($("#vote_value" + message_num).html() === "Up") {
$("#thumbs_up" + message_num).addClass("highlighted");        
$("#thumbs_down" + message_num).removeClass("highlighted");    
} else if ($("#vote_value" + message_num).html() === "Down") {
$("#thumbs_up" + message_num).removeClass("highlighted");        
$("#thumbs_down" + message_num).addClass("highlighted");    
} else {        
$("#thumbs_up" + message_num).removeClass("highighted");         
$("#thumbs_down" + message_num).removeClass("highlighted");    } };




// Revised 

var update_highlight = function (message_num) {    
var thumbs_up = $("#thumbs_up" + message_num);    
var thumbs_down = $("#thumbs_down" + message_num);    
var vote_value = $("#vote_value" + message_num).html();    
var hi = "highlighted";

if (vote_value === "Up") {      
thumbs_up.addClass(hi);        
thumbs_down.removeClass(hi);    
} else if (vote_value === "Down") {        
thumbs_up.removeClass(hi);        
thumbs_down.addClass(hi);    
} else {        
thumbs_up.removeClass(hi);        
thumbs_down.removeClass(hi);    } };
```

Creative Way to Simplify Expressions
```c++
void AddStats(const Stats& add_from, Stats* add_to) {    
add_to->set_total_memory(add_from.total_memory() + add_to->total_memory());    
add_to->set_free_memory(add_from.free_memory() + add_to->free_memory());    
add_to->set_swap_memory(add_from.swap_memory() + add_to->swap_memory());    
add_to->set_status_string(add_from.status_string() + add_to->status_string());    
add_to->set_num_processes(add_from.num_processes() + add_to->num_processes());    ... } 

--------------------------------------------------------------------------------------------

void AddStats(const Stats& add_from, Stats* add_to) {    
#define ADD_FIELD(field) add_to->set_##field(add_from.field() + add_to->field())
ADD_FIELD(total_memory);    
ADD_FIELD(free_memory);    
ADD_FIELD(swap_memory);    
ADD_FIELD(status_string);    
ADD_FIELD(num_processes);    
...    
#undef ADD_FIELD 
} 



```diff
+ tyuyeyresyuryeuytu
- this text is highlighted in red
```

