#Quickly ubuntu-application snippet(PyGtk)

##How to find and kill an app on Quickly / Ubuntu-app. 
```
voidcode@voidcode-Aspire-5750:~$ ps -ax | grep easy-stopwatch 
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html 
23477 pts/0    Sl     0:07 /usr/bin/python bin/easy-stopwatch 
24536 pts/4    S+     0:00 grep --color=auto easy-stopwatch 
voidcode@voidcode-Aspire-5750:~$ kill -9 23477 
```

##Add Ubuntu style to 'toolbar' or other widgets 
toolbar = builder.get_object("toolbar") 
context = toolbar.get_style_context() 
context.add_class(Gtk.STYLE_CLASS_PRIMARY_TOOLBAR)

##Get root path to you app
```
self.rootpath = os.path.split(os.path.abspath(os.path.dirname(__file__)))[0] 
```

##Get the relative path to you /media/data/background.png
```
self.relativepath = os.path.join(os.path.split(os.path.abspath(os.path.dirname(__file__)))[0], '/data/media/', 'background.png')

def appfile(folder, file): 
	    return os.path.join(os.path.abspath(os.path.dirname(__file__)))[0], folder, file)
```

##How to use WebKit in a 'scrolledwindow'-widget
###gets the webkit and the scrolledwindow object. 
```

self.scrolledwindow = builder.get_object("scrolledwindow") 
self.webview = WebKit.WebView()
```

#addes webview to scrolledwindow, then webview.open(url) 
```
self.scrolledwindow.add(self.webview)
self.webview.show()
self.webview.open("http://www.ubuntu.com")
```

##GtkFileChooserDialog with button-handler
###NB:This only returns the path of the select-folder.
```
self.dialog = Gtk.FileChooserDialog() 
self.button = self.dialog.add_button("Select-folder", Gtk.ResponseType.OK) 
self.button.connect("clicked", self.on_clicked_folder) 
self.dialog.set_current_folder('~/') #set start-folder for the FileChooserDialog 
self.dialog.run()

def on_clicked_folder(self, widget): 
	self.dialog.hide() #hide dialog
	print self.dialog.get_current_folder()
```
Output: path to select folder. Like /home/user/Desktop

##Save GtkTextView data in a file
```
viewbuffer = self.builder.get_object("myview").get_buffer() 
file = open("~/test", "w") # “~/test” is the location where the file is being save
file.write(viewbuffer.get_text(viewbuffer.get_start_iter(), viewbuffer.get_end_iter(), include_hidden_chars=True)) 
file.close()
```

##Json: read data from remote url
```
Get bitcoins weighted prices from http://bitcoincharts.com 
import json, urllib2

req = urllib2.Request("http://bitcoincharts.com/t/weighted_prices.json") 
opener = urllib2.build_opener() 
f = opener.open(req) 
self.json = json.loads(f.read()) 
print self.json["USD"]["30d"]
```

##Get clipbord-text 
```
from gi.repository import Gtk, Gdk

clipbord = Gtk.Clipboard.get(Gdk.SELECTION_PRIMARY) 
url = clipbord.wait_for_text()
```

##Get '<title>this</title>' of an webpage
import lxml.html 
```
t = lxml.html.parse("http://www.google.com") 
print t.find(".//title").text
```

