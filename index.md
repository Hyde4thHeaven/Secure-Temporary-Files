## Welcome to 2nd episode of my series **Code for Security**.  

To create temporary files in Python, you’d typically generate a file name using a historical way to create temporary files was to first generate a file name with the **mktemp()** function and then create a file using this name.  
  
**Unfortunately this is not secure**, because a different process may create a file with this name in the time between the call to mktemp() and the subsequent attempt to create the file by the first process. The solution is to combine the two steps and create the file immediately. This approach is used by mkstemp() and the other functions described above.  
  
Recent versions of Python will raise a runtime warning if you call the incorrect method.  
  
## Solution
To creates a temporary file in the most secure manner possible. The file is readable and writable only by the creating user ID. If the platform uses permission bits to indicate whether a file is executable, the file is executable by no one. The file descriptor is not inherited by child processes. **2 secure functions** we use to instead *mktemp()* are **TemporaryFile()** and **mkstemp()**
  
While **TemporaryFile()** return a file-like object that can be used as a temporary storage area. It will be destroyed as soon as it is closed (including an implicit close when the object is garbage collected). Under Unix, the directory entry for the file is either not created at all or is removed immediately after the file is created. Other platforms do not support this; your code should not rely on a temporary file created using this function having or not having a visible name in the file system.  
  
**mkstemp()** returns a tuple containing an OS-level handle to an open file (as would be returned by os.open()) and the absolute pathname of that file, in that order. Raises an auditing event tempfile.mkstemp with argument fullpath.  
  
**The very important different** between *TemporaryFile()* and *mkstemp()* is the user of *mkstemp()* is responsible for deleting the temporary file when done with it.  
  
### Tips  
You can use **tempfile.mkdtemp()** to make the same way in security coding to create a temporary directory!
  
**Another secure function is done!** Secured coding is just a flipped hand when you know the hint!

Let's hunt more vulnerable code to make **Code for Security** next episode. Stay tuned!  
  
**#SecureTempFiles #Code4Sec**  
  
### Ref:
> python.org  
  
______________________________
<table border="0">
 <tr>
   <td> <h3><i>Although my profile picture is quiet, but the real me can make some noise.</i></h3>
      <hr>
      <b><font color="Blue"> Author: Vuttawat Uyanont </font></b>  <br>
      <font color="grey"><i>Sexiest former engineer & banker who interested in Tech, Sake, and Beer.</i></font>  <br>
      <b>Studying:</b> Master Computer Science in Cybersecurity Management at Mahanakorn University.  <br> </td>  
   <td><img src="Author.png" width="150"/></td>  
 </tr>
</table>
  
