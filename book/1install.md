# 1.0 Debugging in XOOPS

XOOPS has three levels of debugging; PHP debug, MySQL debug and Smarty debug.

If you suspect that your site may have faults there are several tools built into XOOPS that can help diagnose the problem.

### 1.1 	PHP Debug

The first is PHP Debug Mode that enables PHP errors to show on the screen.

If PHP debug is not on, the system will suppress error messages coming from the PHP code.

This is the main reason for the dreaded "Blank Page" problem, which is caused by an error in the PHP code, so serious that the interpretation of the code can no longer continue.

Enabling PHP debug will often result in these blank pages showing an error message instead.

**1.2 	MySQL Debug**

The second tool is Mysql/Blocks Debug. This gives a popup out put of MySQL queries as well as other useful information.

With this debugging setting enabled, a window will popup after each page load, showing the database queries, executed on the page. It will also show which blocks and templates are used on the page along with caching information (whether the block or template is cached)

Faulty SQL queries will be highlighted in red with a MySQL error message appended

**1.3 	Smarty Debug**

The third tool built into Xoops is the Smarty Templates Debug mode. It is very useful not only for troubleshooting problems but also to assist in design of themes and templates. It shows the Smarty Variables and what they are assigned to on a given page.

Smarty debug settings will open a new window on all pages using Smarty templates, showing all variables assigned to Smarty along with their values. This debug setting is useful if you know that there are no PHP errors, that the SQL queries execute successfully, but the information does not show up as expected. Quite often it is a matter of organising the information correctly for display which is only discovered by looking at the actual values in each Smarty variable. An example is information in an array, which the template is coded to take from a sub-array instead - or vice versa.

**1.4 	Setting XOOPS Debugging**

As default, the Debug Mode is set to off. In order to activate Debug in XOOPS, please go to the menu:
Preferences  System Options  General Settings:
 
***Figure 1: Selecting XOOPS General Settings***

This will open the General Settings form, where you can find the options for Debug Mode:
 
 
***Figure 2: Selecting Debug Mode***

Most of the time, we select the first option: “Enable debug (inline mode)”.
Once this done, XOOPS will show all debug information at the bottom of the page:

 
***Figure 3: Control Admin Side***

 
***Figure 4: Front Side***

**1.4.1	Changing XOOPS Debug Mode directly in the database**

What to do when you don’t have access to the Admin to set the Debug mode there, e.g. when there are bugs that cause a “blank screen of death”?
There are two ways to change the XOOPS Debug Mode: 

1. You can do it directly in phpMyAdmin
2. You can run a MySQL query to 

```
UPDATE XXXX_config SET conf_value=YYYY WHERE conf_modid=0 AND conf_catid=1 AND conf_name='debug_mode'```


Replace XXXX with the value of XOOPS_DB_PREFIX in mainfile.php (default is "xoops").

Replace YYYY (Debug Mode) with:

0, for Off

1, for Debug Inline mode

2, for Debug in pop-up mode

3, for Smarty Template Debug

**1.4.2	Setting Configuration**

Now the problem is that these messages will be visible to all users. But if we don’t want that, then XOOPS offers following configuration option, stored in

/xoops_data/configs/xoopsconfig.php

Just select the right debug level that you want by keeping the “0” or replacing it with “1” or “2”:

```
        /**#@+
         * Debug level for XOOPS
         *
         * <ul>Displaying debug information to different level(s) of users:
         *  <li> 0 - To all users</li>
         *  <li> 1 - To members</li>
         *  <li> 2 - To admins only</li>
         * </ul>
         */
	    /**#@-*/
        **"debugLevel" => 0,**```


