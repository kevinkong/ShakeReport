# SRReport

SRReport is a small library which make easy for your testers to report bugs.
Shake the iDevice, and they will send:

* a screenshot of the current view
* the logs of the current session
* the crash report if a crash has been reported
* the dumped view hierarchy

# Installation

Add those frameworks to your target:

* QuartzCore
* MessageUI

Copy the `library` folder in your project.

Include `SRReporter.h`

Then, copy this line to start the reporter:

	- (BOOL)application:(UIApplication *)application 
			didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
	{
   		[[SRReporter reporter] startListener]; //this line starts the reporter
   		return YES;
	}
	

# Usage

**Shake** the iDevice when you want to report something. A Mail Composer view will appear with all the information that will be send. The tester can add some explanation, and change the recipient of the email.

# Configurations
You can configure a little the reporter in order to set the default email address which will receive the report, and enable/disable the HTML report:

	SRReporter *reporter = [SRReporter reporter];
    [reporter setDefaultEmailAddress:@"templier.jeremy@gmail.com"];
	//[reporter setUseHTMLReport:NO];   // default is YES
    [reporter startListener];


# Demo App
<!-- MacBuildServer Install Button -->
<div class="macbuildserver-block">
    <a class="macbuildserver-button" href="http://macbuildserver.com/project/github/build/?xcode_project=ShakeReport.xcodeproj&amp;target=ShakeReport&amp;repo_url=git%3A%2F%2Fgithub.com%2Fjayztemplier%2FShakeReport.git&amp;build_conf=Release" target="_blank"><img src="http://com.macbuildserver.github.s3-website-us-east-1.amazonaws.com/button_up.png"/></a><br/><sup><a href="http://macbuildserver.com/github/opensource/" target="_blank">by MacBuildServer</a></sup>
</div>
<!-- MacBuildServer Install Button -->

# Use it with a Backend
You can also use Shake Report with a backend. And guess what!? It's open source too!
https://github.com/jayztemplier/ShakeReportServer

To send the reports to the server, setup the listener like that:
	
    SRReporter *reporter = [SRReporter reporter];
    // Send data to a Server instead of displaying the mail composer
    NSURL *url = [NSURL URLWithString:@"http://localhost:3000/reports.json"];
    [reporter startListenerConnectedToBackendURL:url];

# License
SRReport is available under the MIT license. See the LICENSE file for more info