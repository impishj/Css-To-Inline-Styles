The task of mobile friendly email design seems like it's going to be painful.  
This is my attempt to make it cleaner.  

This update adds the ability to add outlook conditional comments via a <mobile> tag. 

This inliner now interprets this (<mobile> tag):  

`
<mobile>
The content here will only be visiable on mobile devices
</mobile>
`
as this:
`
<!--<![if mso]-->
<div class="show-mobile" style="display:none; width:0px; max-height:0px; overflow:hidden; mso-hide:all; line-height: 0px;" >
The content here will only be visiable on mobile devices
</div>
<!--<![endif]-->
`

the .hide-mobile class can be used to hide elements from mobile clients.
[small]however for it to work in gmail it must be a div element it can't be a table element (because gmail converts them to divs and I'm guessing the inline style is lost there)[/small]

`
                        .show-mobile{
                          display:none;
                          width:0px;
                          max-height:0px;
                          overflow:hidden;  
                          mso-hide:all;
                          line-height: 0px;
                        }

                        @media only screen and (max-device-width: 480px) {

                            body[yahoo] .show-mobile {
	                            display:block !important;
	                            margin: 0;
	                            padding:0;
	                            overflow : visible !important;
	                            width:auto !important;
	                            max-height:inherit !important;
	                            line-height: auto !important; 
                            }

                            body[yahoo] .hide-mobile{
								display:none;
								width:0px;
								max-height:0px;
								overflow:hidden;
								overflow:hidden !important;
                            }
						}
`

General information about the inliner:

https://github.com/impishj/Css-To-Inline-Styles

Css To Inline Styles.app

Usage: 
1. Drag a html file on Css To Inline Styles.app (on the doc or wherever you place the file.)
2. Copy the output in the window

Credits:
Jeremy Sewell Made this with Platypus in about an hour! (Uptate: several hours) http://sveinbjorn.org/platypus/

Based on Tijs Verkoyen's CssToInlineStyles class. which can be found here: http://classes.verkoyen.eu/css_to_inline_styles

Tijs Verkoyen is not in any way associated with this application.

Licence for the OSX application:
Jeremy Sewell releases this thing into the public Domain, it's free, just don't redistribute for commercial purposes.


Licence for the php class contained within the application:

The PHP Script CssToInlineStyles class is Copyright©, Tijs Verkoyen. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

Neither the name of Tijs Verkoyen, nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
This software is provided by the copyright holders and contributors as is and any express or implied warranties, including, but not limited to, the implied warranties of merchantability and fitness for a particular purpose are disclaimed. In no event shall the copyright owner or contributors be liable for any direct, indirect, incidental, special, exemplary, or consequential damages (including, but not limited to, procurement of substitute goods or services; loss of use, data, or profits; or business interruption) however caused and on any theory of liability, whether in contract, strict liability, or tort (including negligence or otherwise) arising in any way out of the use of this software, even if advised of the possibility of such damage.

Licence information: http://classes.verkoyen.eu/css_to_inline_styles