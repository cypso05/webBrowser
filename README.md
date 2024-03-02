# The script for a basic web browser application written in Python using the PyQt5 framework.

The script for a basic web browser application written in Python using the PyQt5 framework.

This code is a simple web browser application built using PyQt5, which allows the user to browse the web, navigate between web pages, extract content, save web pages as PDF or Word documents, search keywords, download files, and open links in new tabs or windows.I develiped this for educational purposes to demonstrate how to create a web browser with tabs, navigation buttons, and some extra features like saving pages as PDF and word format meant for internal purposes..

The browser displays web pages in QWebEngineView tabs. It has a toolbar with buttons to navigate back/forward, reload, go home, and open new tabs. The URL bar shows the current page URL and allows entering URLs to navigate to.

The main Browser class inherits from QMainWindow to create the application window. In the init method, it sets up the window, toolbar, tab widget, URL bar, and buttons. Actions are created for each button, connected to methods like navigate_back(), navigate_forward(), etc. which control page navigation in the browser tabs.

When a new tab is opened, a QWebEngineView is created to display the web page content, and a BrowserWebEnginePage is set as its page. This allows hooking into events like link hovering and context menus. New tabs open to a default URL like Google.

# I have attached a fully functional version of the script WebBrowser.py  that can be delopyed to any windows system for testing purposes via any IDE that supports Python (feel the power of python and the PyQt5 web engine). The script can be improved and does need some adjustments and additional features to be used for production.
# Remember to pip install necessary or missing import or packages before testing the script. Happy coding!!!!

sys and os modules are imported for system-related functionalities.
time module is imported for time-related functionalities.
requests module is imported for making HTTP requests.
QUrl, QEvent, QTimer are imported from PyQt5.QtCore for handling URLs, events, and timers.
QApplication, QMainWindow, QToolBar, QLineEdit, QAction, QVBoxLayout, QWidget, QFileDialog, QInputDialog, QMenu, QTabWidget, QPushButton, QMessageBox are imported from PyQt5.QtWidgets for building the GUI.
QWebEngineView, QWebEnginePage are imported from PyQt5.QtWebEngineWidgets for embedding a web browser view in the application.
QImage, QPainter are imported from PyQt5.QtGui for handling images and painting.
QPrinter is imported from PyQt5.QtPrintSupport for printing functionalities.
Document is imported from docx for creating Word documents.
The Browser class is defined, which inherits from QMainWindow. This class represents the main window of the web browser application.

The __init__ method is the constructor of the Browser class. It initializes the main window and sets up the UI components.

The title of the window is set to "Web Browser".
A QTabWidget is created to hold multiple tabs for browsing different web pages. It is set to allow closing tabs.
A QLineEdit is created as the URL bar where the user can enter the URLs they want to navigate to.
Several actions are created for various functionalities like navigating back/forward, reloading the page, going home, extracting content, saving as PDF/Word, searching keywords, and downloading files.
A QToolBar is created to hold these actions and the URL bar.
A layout is created to arrange the toolbar and tab widget vertically.
A container widget is created to hold the layout, and it is set as the central widget of the main window.
The currentChanged signal of QTabWidget is connected to a slot that updates the URL bar with the current tab's URL.
Margins of the layout are set to 0 for removing any extra space around the toolbar and tab widget.
The create_action method is a utility method to create a QAction with the given text and slot.

The add_actions_to_toolbar method adds the actions to the toolbar.

The on_current_tab_changed method is a slot that gets called when the current tab changes. It updates the URL bar with the current tab's URL.

The update_urlbar method updates the URL bar with the given URL.

The create_new_tab_button method creates a button for creating new tabs.

The create_new_tab method creates a new tab with a QWebEngineView widget to display web content.

BrowserWebEnginePage is used as the page for the QWebEngineView widget, which is a subclass of QWebEnginePage and handles opening new tabs.
Various signals are connected to corresponding slots for handling URL changes, loading finished, and link hovering.
JavaScript code is injected into the web page to handle fullscreen video playback.
The tab is added to the QTabWidget.
The close_tab method is a slot that gets called when a tab is requested to be closed. It removes the tab from the QTabWidget.

The remaining methods are slots for various functionalities of the web browser:

navigate_back, navigate_forward, and reload_page handle the corresponding actions.
navigate_to_url is called when the user presses Enter in the URL bar. It creates a new tab with the entered URL.
update_title updates the title of the current tab to the page title.
go_home loads Google's homepage in the current tab.
extract_content is called to extract media content (videos) from the current page's HTML.
save_as_pdf saves the current page as a PDF file.
take_screenshot_and_save_as_pdf captures a screenshot of the current page and saves it as a PDF file.
