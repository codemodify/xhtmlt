
### What is it
R&D Project to have an alternative markup language for xHTML based on XSLT

Origin -> http://ukoreh.github.io -> AppKit() -> POC

### Example
http://ukoreh.github.io/appkit/pocdemo.xml

### The Vision
	The model of web-development in today's times is wrong.
    The "web-development" concept is wrong by it self.
    
    There is no web development or desktop development.
    That is a narrow and afirmation taken out of the context of the development.
    
    There is only development and applicatioins.
    The same app can have many UI but only one implementation logic.

    The web development is all about UI, and thus unexperienced people
    rushing for quick money - dragged the whole stream after them, only to show 
    a "js-animation" trick that lasts for 20 years now. No progress there.
    One of the reasons for this is lack of synchronization between main players
    in the field that have "pushed" their solutions (ASP, ASPX, JSP, PHP) in 
    the wrong-from-the-start development approach. All the templating solutions 
    like "smartty", "pear", "asp", "jsp",etc and alike in any corresponding 
    language are just hacks to workaround the created situation.

    This project tries to define a set of components to enable a logic written in
    any language to have its UI on the web as is specified in the app's policy.
    
    Ex:
    having an app in C++, we want it to have the UI side done in:
    - (a) flash for mobile devices
    - (b) HTML/CSS/JS for internal company's webserver
    - (c) QT for desktop apps
    - (d) any other custom UI approach
    - (e) etc

    This set of components(code base) focuses on point (b) so we can finally put an end
    to the ammateur world of the prorammers/designers that do something that they 
    do not understand roots of which are comming from.

#### Why do it this way ?
    ------------------------------------------------------------
    - because it is the only correct and solid way of doing things
    - because there is no need to have hacks invented that bloat your 
      code/logic and don't do anything than addressing some narrow problem 
      not related to the product
      (ex1: how to add 2px more to left or right to make it look better)
      (ex2: write some templating language speciffic code that later blocks you into a speciffic range of limits)
    - because you use HTML/CSS/JS for interfacing your app's logic and YourLanguage/ThisLibrary 
      for having a rock solid modular logic where you free your hands to implement any 
      programming techniques at your needs.
      
      
#### How the development of the components goes or started
    ------------------------------------------------------------
    It is the oposite in a way of reversing the traditional way. Meaning first we write
    some meta code that must be simple and straghtforward in usage with no bloating, then we find
    an appropriate implementation for that metacode.
    Ex:
        I want in HTML to have grids/tables that can help me build quickly a page like this:

```xml
<page>
	<grid class="widthEghtyPercent alignCenter">
		<row>
			<cell>
				<image source="...." ></image>
				<text>That is a cool picture</text>
			</cell>
			<cell>
				<hyperLink url="http://www.google.com">
					<image source="http://www.google.com/logos/google.gif" ></image>
					<text>Google Search</text>
				</hyperLink>
			</cell>
		</row>
	</grid>
</page>
```

		For page look and feel
            we write some CSS files wehere we define all that is needed to have 
            class="widthEghtyPercent alignCenter" working.
        
        For page content definition 
            we write some XSLT files to define all the tags above.

        Now at this point this gives you a code base that lets you build clean pages with rich content.
        As example this code base may use as back end the Yahoo UI library, or any other more fancy 
        implementations if available.
        
        So how to bind all these into a C++ app for example ?
        Here we have 2 cases to solve:
        1 - "The C++ app needs to publish data" - that is easy because it will use the same CSS/XSLT 
            codebase, we'll need to provide some wrappers for this in the C++ side to make it easy 
            to operate with this codebase. As an example we might just create a project called QtWeb - 
            a set of widgets that have the same name as all the Qt types but their implementation spit 
            out CSS/XSLT code that will be transformet into HTML later. This will give a powefull 
            featture for all the Qt apps out there: the same Qt code will compie as binary executable 
            for the all the OS supported, also the same code will compile and output HTML represenation 
            of the widgets. That is neat. Now how about having a way to get input from the user that has 
            interacted with the controls on the page ?
            
        2 - "The C++ apps needs input data from the published data" - that is achieved by having 
            model/view approach. We'll keep two copies of data and we'll synch between them. One will 
            be kept at te client side by the JsKit, another will be kept by out app. 
            The synchronisation is done by traditional HTTP requests. Btw this implies a natural 
            tehcnique that is so natural that other missed its real obvious usage and started flames 
            about calling it AJAX. That is because as I mentioned above: people took a wrong way in 
            developing applicaitons, and ended up calling themselves "masters of web-delopement". 
            While there is no such thing except a wise and correct development - they probably meant 
            masters of hacking in the wrong direction of a imature tehcnology that is nothing more 
            than a temporary stage of mutation into something to have MVC at its core later on.
