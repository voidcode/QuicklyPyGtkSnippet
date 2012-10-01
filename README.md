#QuicklyPyGtkSnippet
===================

Just some code-snippet for [Ubuntu App Development](http://developer.ubuntu.com/showdown/workshops/).

Focus is on Python Gtk and Quickly.


##Add Ubuntu style to 'toolbar' or other widgets 
```
toolbar = builder.get_object("toolbar") 
context = toolbar.get_style_context() 
context.add_class(Gtk.STYLE_CLASS_PRIMARY_TOOLBAR)
```

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
gets the webkit and the scrolledwindow object. 

addes webview to scrolledwindow, then webview.open(url)  
```
self.scrolledwindow = builder.get_object("scrolledwindow") 
self.webview = WebKit.WebView()

self.scrolledwindow.add(self.webview)
self.webview.show()
self.webview.open("http://www.ubuntu.com")
```


##GtkFileChooserDialog with button-handler
NB:This only returns the path of the select-folder.

Output: path to select folder. Like /home/user/Desktop
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


##Save GtkTextView data in a file
```
viewbuffer = self.builder.get_object("myview").get_buffer() 
file = open("~/myfile", "w") # “~/test” is the location where the file is being save
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
Output: last select text
```
from gi.repository import Gtk, Gdk

clipbord = Gtk.Clipboard.get(Gdk.SELECTION_PRIMARY) 
print url = clipbord.wait_for_text()
clipboard.store()
```


##Get title of an webpage
Wee only need an url.
```
import urllib2
from BeautifulSoup import BeautifulSoup

html = urllib2.urlopen("http://www.ubuntu.com").read()
soup = BeautifulSoup(html)
print soup.title.string
```

If you don´t need to retrive the title from https site, you can use lxml.
```
import lxml.html 

t = lxml.html.parse("http://www.ubuntu.com") 
print t.find(".//title").text 
```

