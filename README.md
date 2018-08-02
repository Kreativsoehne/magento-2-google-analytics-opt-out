# magento-2-google-analytics-opt-out
Magento 2 extension to give customers the ability to opt-out Google Analytics tracking. Useful for european union's countries (GDPR)

## installation
    1. $ composer require kreativsoehne/magento-2-google-analytics-opt-out
    2. $ ./bin/magento module:enable kreativsoehne_AnalyticsOptout
    3. $ ./bin/magento cache:clean
    4. Profit.

## usage
After installing and activating, you can place a simple deactivation checkbox nearly everywhere you want.

This is how you do it for a CMS page:

	Content -> Elements -> Pages -> <edit page>

Reveal the Content part and switch Editor to markup mode. After that, place the following code anywhere you want.

	<p><input class="ga-optout" type="checkbox" /> disable Google Analytics</p>
	<p>{{block class="Magento\Framework\View\Element\Template" name="gaoptout" template="kreativsoehne_AnalyticsOptout::gaoptout.phtml"}}</p>

Clear the cache 

	$ ./bin/magento cache:clean

and open up that page on the frontend wihin a browser.
You are now able to check and un-check a checkbox which will result in Google Analytics not tracking you on that browser.

## how it works
This extension simply provides a small Template with some simple Java Script which can be placed anywhere via Magento's block feature.
When checking the checkbox, a Java Script generates a cookie called "ga-disable-<Google Analytics ID>", which forces Google Analytics to stop collecting data.
When un-checkig, the previously generated cookie will be deleted.

## notice:
This Extension may not work in the future when new versions of google analytics with differend functionality appear.