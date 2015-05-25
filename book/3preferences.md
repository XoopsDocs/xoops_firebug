# 3.0 PHP Debugging without XOOPS

####3.1 	History

Frankblack was frustrated with debugging his AJAX applications using just the standard Debug Mode, therefore he ended up using FireBug + FirePHP as addons for Firefox, and he rewrote XOOPS class/logger/render.php to output the XOOPS debug messages to FirePHP, resulting in a very flexible solution. Trabis contributed as well, and now we have a solution that is very helpful to XOOPS Developers.

####3.2 	Installation

Important – you have to have Firefox to use Firebug and FirePHP! Recommended: Ver. 4.0

There are few simple steps to get you going:

1. Download and install in Firefox the newest version of Firebug (currently 1.7) from here: http://getfirebug.com/
2. Download and install in Firefox the latest version of FirePHP extension: 
https://addons.mozilla.org/en-US/firefox/addon/firephp/
3.	Download and install the FireDebug 1.6 for XOOPS 2.5.x
4.	Go to xoops_data/configs/xoopsconfig.php and change the DebugLogger configuration to:


        /**#@+
         * Debug logger for XOOPS
         *
         * <ul>Choose logger to use
         *  <li> legacy </li>
         *  <li> pqp </li>
         *  <li> firephp </li>
         * </ul>
         */
        "debugLogger" => firephp,
        /**#@-*/
and you’re ready to go.

####3.3 	Using FirePHP/Firebug with XOOPS

After installing the above tools, you can add this line your PHP file:

```
require_once XOOPS_ROOT_PATH.'/class/logger/firephp/FirePHPCore/fb.php';```

and you can start sending messages to FirePHP:
```
FB::log('Log message');
FB::info('Info message');
FB::warn('Warn message');
FB::error('Error message');
FB::trace('Trace message');
```
Figure 7: Firebug with FirePHP and XOOPS debug messages

The messages from XOOPS are coming from XOOPS Debug, but XOOPS just redirects them to Firebug, so you have all debug messages conveniently in one location. 

   
**Figure 8: XOOPS Debug messages in XOOPS**

**Figure 9: XOOPS Debug messages in Firebug**

Additional advantage is that you also have Smarty Debug Output as well – all in one location.
When we want to see values of variables, we can send it as well, e.g.

```
FB::log($index_admin,'this is our ModuleAdmin class'); ```


This will show in Firebug as:

 

Since there is more information than the line can hold, we can just click on that line and a new window will open with all the details:
 
**Figure 10: Firebug with detailed FirePHP variable info**
