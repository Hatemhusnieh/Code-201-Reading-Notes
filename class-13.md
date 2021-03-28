# Local Storage
* **Storage** for **Web Applications** was always something that is missing and not satisfactory. That was of-course before `HTML5` was invented.  

* **Cookies** were not a consistent solution, that's because:  
    - **Cookies** are included with every **HTTP** request, thereby slowing down your web application by needlessly transmitting the same data over and over
    - **Cookies** are included with every **HTTP** request, thereby sending data un-encrypted over the internet (unless your entire web application is served over **SSL**)
    - **Cookies** are limited to about **4 KB** of data — enough to slow down your application, but not enough to be terribly useful

* The goal was to have a lot of storage space on the client that persists beyond a page refresh and isn’t transmitted to the server.

## INTRODUCING HTML5 STORAGE
`HTML5` Storage is a way for web pages to store named key/value pairs locally, within the client web browser. Like cookies, this data persists even after you navigate away from the web site, close your browser tab, exit your browser, or what have you.

* almost al browsers support `HTML5` storage.  

## USING HTML5 STORAGE
You store data based on a named key, then you can retrieve that data with the same key. The named key is a string. The data can be any type supported by JavaScript, including strings, Booleans, integers, or floats.

* use  `parseInt()` or `parseFloat()` to convert **Strings** into **integers** or **floats**

* **Local Storage** can be treated like an **Object**, where you can access its properties by square brackets.

* To remove the value for a given named key, and clearing the entire storage area:  
```
interface Storage {
  deleter void removeItem(in DOMString key);
  void clear();
};

```

* To get the total number of values in the storage area, and to iterate through all of the keys by index:  
```
interface Storage {
  readonly attribute unsigned long length;
  getter DOMString key(in unsigned long index);
};
```

## TRACKING CHANGES TO THE HTML5 STORAGE AREA
You can track changes in storage area, trap the storage event. 

The storage event is fired on the window object whenever `setItem()`, `removeItem()`, or `clear()` is called and actually changes something.

The storage event is not cancelable. From within the handle_storage callback function, there is no way to stop the change from occurring.

## LIMITATIONS IN CURRENT BROWSERS
**5 megabytes** : This is how much storage space each origin gets by default. Knowing of-course that you’re storing strings, not data in its original format.

**QUOTA_EXCEEDED_ERR** : is the exception that will get thrown if you exceed your storage quota of 5 megabytes.


