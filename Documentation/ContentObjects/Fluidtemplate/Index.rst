.. ==================================================
.. FOR YOUR INFORMATION
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.

.. include:: ../../Includes.txt


.. _cobj-fluidtemplate:

FLUIDTEMPLATE
^^^^^^^^^^^^^

The TypoScript object FLUIDTEMPLATE works in a similar way to the
regular "marker"-based :ref:`TEMPLATE <cobj-template>` object. However, it does not use
markers or subparts, but allows Fluid-style variables with curly
braces.


.. _cobj-fluidtemplate-properties:

Properties
""""""""""

.. _cobj-fluidtemplate-properties-templatename:

templateName
''''''''''''

.. container:: table-row

   Property
         templateName

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         This name is used together with the set format to find the template in the given
         templateRootPaths. Use this property to define a content object, which should be
         used as template file. It is an alternative to ".file". If ".template" is set,
         it takes precedence.

         **Example:**

         .. code-block:: typoscript

			lib.stdContent = FLUIDTEMPLATE
			lib.stdContent {
				templateName = Default
				layoutRootPaths {
					10 = EXT:frontend/Resources/Private/Layouts
					20 = EXT:sitemodification/Resources/Private/Layouts
				}
				partialRootPaths {
					10 = EXT:frontend/Resources/Private/Partials
					20 = EXT:sitemodification/Resources/Private/Partials
				}
				templateRootPaths {
					10 = EXT:frontend/Resources/Private/Templates
					20 = EXT:sitemodification/Resources/Private/Templates
				}
				variables {
					foo = bar
				}
			}

         **Example:**

         .. code-block:: typoscript

			lib.stdContent = FLUIDTEMPLATE
			lib.stdContent {
				templateName = TEXT
				templateName.stdWrap {
					cObject = TEXT
					cObject {
						data = levelfield:-2,backend_layout_next_level,slide
						override.field = backend_layout
						split {
							token = frontend__
							1.current = 1
							1.wrap = |
						}
					}
					ifEmpty = Default
				}
				layoutRootPaths {
					10 = EXT:frontend/Resources/Private/Layouts
					20 = EXT:sitemodification/Resources/Private/Layouts
				}
				partialRootPaths {
					10 = EXT:frontend/Resources/Private/Partials
					20 = EXT:sitemodification/Resources/Private/Partials
				}
				templateRootPaths {
					10 = EXT:frontend/Resources/Private/Templates
					20 = EXT:sitemodification/Resources/Private/Templates
				}
				variables {
					foo = bar
				}
			}


.. _cobj-fluidtemplate-properties-template:

template
''''''''

.. container:: table-row

   Property
         template

   Data type
         :ref:`cObject <data-type-cobject>`

   Description
         Use this property to define a content object, which should be
         used as template file. It is an alternative to ".file"; if
         ".template" is set, it takes precedence. While any content object
         can be used here, the cObject :ref:`FILE <cobj-file>` might be the
         usual choice.


.. _cobj-fluidtemplate-properties-file:

file
''''

.. container:: table-row

   Property
         file

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         The fluid template file. It is an alternative to
         ".template" and is used only, if ".template" is not set.


.. _cobj-fluidtemplate-properties-templaterootpaths:

templateRootPaths
'''''''''''''''''

.. container:: table-row

   Property
         templateRootPaths

   Data type
         array of file paths with :ref:`stdWrap <stdwrap>`

   Description
         .. note::

            Mind the plural -s in "templateRootPaths"!

         Used to define several paths for templates, which will be tried
         in reversed order (the paths are searched from bottom to top).
         The first folder where the desired layout is found, is used.
         If the array keys are numeric, they are first sorted and then
         tried in reversed order.

         Useful in combination with the :ref:`templateName <cobj-fluidtemplate-properties-templatename>`
         property.

         **Example:**

         .. code-block:: typoscript

			page.10 = FLUIDTEMPLATE
			page.10.templateName = Default
			page.10.templateRootPaths {
				10 = EXT:sitedesign/Resources/Private/Layouts
				20 = EXT:sitemodification/Resources/Private/Layouts
			}


.. _cobj-fluidtemplate-properties-layoutrootpath:

layoutRootPath
''''''''''''''

.. container:: table-row

   Property
         layoutRootPath

   Data type
         file path /:ref:`stdWrap <stdwrap>`

   Description
         Sets a specific layout path; usually it is Layouts/ underneath the
         template file.


.. _cobj-fluidtemplate-properties-layoutrootpaths:

layoutRootPaths
'''''''''''''''

.. container:: table-row

   Property
         layoutRootPaths

   Data type
         array of file paths with :ref:`stdWrap <stdwrap>`

   Description
         .. note::

            Mind the plural -s in "layoutRootPaths"!

         Used to define several paths for layouts, which will be tried
         in reversed order (the paths are searched from bottom to top).
         The first folder where the desired layout is found, is used.
         If the array keys are numeric, they are first sorted and then
         tried in reversed order.

         **Example:**

         .. code-block:: typoscript

			page.10 = FLUIDTEMPLATE
			page.10.file = EXT:sitedesign/Resources/Private/Templates/Main.html
			page.10.layoutRootPaths {
				10 = EXT:sitedesign/Resources/Private/Layouts
				20 = EXT:sitemodification/Resources/Private/Layouts
			}

         If property :ref:`layoutRootPath <cobj-fluidtemplate-properties-layoutrootpath>`
         (singular) is also used, it will be placed as the first option
         in the list of fall back paths.


.. _cobj-fluidtemplate-properties-partialrootpath:

partialRootPath
'''''''''''''''

.. container:: table-row

   Property
         partialRootPath

   Data type
         file path /:ref:`stdWrap <stdwrap>`

   Description
         Sets a specific partials path; usually it is Partials/ underneath the
         template file.


.. _cobj-fluidtemplate-properties-partialrootpaths:

partialRootPaths
''''''''''''''''

.. container:: table-row

   Property
         partialRootPaths

   Data type
         array of file paths with :ref:`stdWrap <stdwrap>`

   Description
         .. note::

            Mind the plural -s in "partialRootPaths"!

         Used to define several paths for partials, which will be tried
         in reversed order. The first folder where the desired partial is
         found, is used. The keys of the array define the order.

         See :ref:`layoutRootPaths <cobj-fluidtemplate-properties-layoutrootpaths>`
         for more details.


.. _cobj-fluidtemplate-properties-format:

format
''''''

.. container:: table-row

   Property
         format

   Data type
         keyword /:ref:`stdWrap <stdwrap>`

   Description
         Sets the format of the current request.

   Default
         html


.. _cobj-fluidtemplate-properties-extbase-pluginname:

extbase.pluginName
''''''''''''''''''

.. container:: table-row

   Property
         extbase.pluginName

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         Sets variables for initializing extbase.


.. _cobj-fluidtemplate-properties-extbase-controllerextensionname:

extbase.controllerExtensionName
'''''''''''''''''''''''''''''''

.. container:: table-row

   Property
         extbase.controllerExtensionName

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         Sets the extension name of the controller.


.. _cobj-fluidtemplate-properties-extbase-controllername:

extbase.controllerName
''''''''''''''''''''''

.. container:: table-row

   Property
         extbase.controllerName

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         Sets the name of the controller.


.. _cobj-fluidtemplate-properties-extbase-controlleractionname:

extbase.controllerActionName
''''''''''''''''''''''''''''

.. container:: table-row

   Property
         extbase.controllerActionName

   Data type
         string /:ref:`stdWrap <stdwrap>`

   Description
         Sets the name of the action.


.. _cobj-fluidtemplate-properties-variables:

variables
'''''''''

.. container:: table-row

   Property
         variables

   Data type
         *(array of cObjects)*

   Description
         Sets variables that should be available in the fluid template. The
         keys are the variable names in Fluid.

         Reserved variables are "data" and "current", which are filled
         automatically with the current data set.


.. _cobj-fluidtemplate-properties-settings:

settings
''''''''

.. container:: table-row

   Property
         settings

   Data type
         *(array of keys)*

   Description
         Sets the given settings array in the fluid template. In the
         view, the value can then be used.

         **Example:**

         .. code-block:: typoscript

			page = PAGE
			page.10 = FLUIDTEMPLATE
			page.10 {
				file = fileadmin/templates/MyTemplate.html
				settings {
					copyrightYear = 2013
				}
			}

         To access copyrightYear in the template file use this:

         .. code-block:: text

         	{settings.copyrightYear}

         Apart from just setting a key-value pair as done in the example,
         you can also reference objects or access constants as well.


.. _cobj-fluidtemplate-properties-dataprocessing:

dataProcessing
''''''''''''''

.. container:: table-row

   Property
         dataProcessing

   Data type
         *(array of class references by full namespace)*

   Description
         Add one or multiple processors to manipulate the ``$data`` variable
         of the currently rendered content object, like tt_content or page.
         The sub-property ``options`` can be used to add further parameter to the processor class.

         **Example:**

         .. code-block:: typoscript

			my_custom_ctype = FLUIDTEMPLATE
			my_custom_ctype {
				templateRootPaths {
					10 = EXT:your_extension_key/Resources/Private/Templates
				}
				templateName = CustomName
				settings {
					extraParam = 1
				}
				dataProcessing {
					1 = Vendor\YourExtensionKey\DataProcessing\MyFirstCustomProcessor
					2 = Vendor2\AnotherExtensionKey\DataProcessing\MySecondCustomProcessor
					2 {
						options {
							myOption = SomeValue
						}
					}
				}
			}


.. _cobj-fluidtemplate-properties-stdwrap:

stdWrap
'''''''

.. container:: table-row

   Property
         stdWrap

   Data type
         :ref:`->stdWrap <stdwrap>`


[tsref:(cObject).FLUIDTEMPLATE]


.. _cobj-fluidtemplate-examples:

Example:
""""""""

The Fluid template (in fileadmin/templates/MyTemplate.html) could look
like this:

.. code-block:: html

	<h1>{data.title}<f:if condition="{data.subtitle}">, {data.subtitle}</f:if></h1>
	<h3>{mylabel}</h3>
	<f:format.html>{data.bodytext}</f:format.html>
	<p>&copy; {settings.copyrightYear}</p>

You could use it with a TypoScript code like this:

.. code-block:: typoscript

	page = PAGE
	page.10 = FLUIDTEMPLATE
	page.10 {
		template = FILE
		template.file = fileadmin/templates/MyTemplate.html
		partialRootPath = fileadmin/templates/partial/
		variables {
			mylabel = TEXT
			mylabel.value = Label coming from TypoScript!
		}
		settings {
			# Get the copyright year from a TypoScript constant.
			copyrightYear = {$year}
		}
	}

As a result the page title and the label from TypoScript will be
inserted as headlines. The copyright year will be taken from the
TypoScript constant "year".

