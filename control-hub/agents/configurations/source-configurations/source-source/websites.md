# Websites

Connect your Website source to Aiimi Insight Engine to make the most of your data. Once you have selected a Source System type more detail will expand to customise this.\
General

1. Enter the URL within the website to crawl in to Start Website URLs.
2. Choose the credentials to use, this will contain both the Username and Password used to connect to Website.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
3. Enter the other page URLs that need indexing within Crawl pages with these URLs.
   * Any URLs you don't want to crawl should be added to Do not crawl pages with these URLs.
4. You can choose the level of links the crawl will follow within Distance from start URLs to crawl.
   * 0 Will stay within the page it is on.
   * 1 will follow the links on the start page.
   * 2 will then follow the links on their pages.
   * -1 will perform unlimited link scanning.
5. To exclude URLs from indexing but still crawled enter the URLs within Exclude these URLs from being indexed.
6. To ensure only websites are crawled check and enter any extensions in Valid web page extensions. This will stop any documents being scanned as a website.
7. Enter the User Agent, if left blank the default will be used.
8. Enable Dynamic Expansion in order to expand placeholders in the start URLs.
9. Enable regular expressions for inclusions and exclusions to use RegEx.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-23 at 14.25.50.png" alt=""><figcaption></figcaption></figure>

#### Crawl Details

1. Between page load crawling, you can set a delay within Page crawl delay in milliseconds.
   * This allows you to control the crawl rate and it can prevent DOS.
2. Limit the number of pages crawled within Maximum pages to crawl.
   * Leaving this as -1 means there is no limit.
3. Set the Page timeout in seconds. This will determine how long to wait before timing out a loading page.

#### Created Date

1. Determine the date you want to be used for page Created.
   * Null (Left Blank)
   * Modified Date
   * Crawled Date
   * Meta Tags
   * RegEx
2. If you have selected Meta Tags or RegEx enter the name in Meta Tag/ Regex.
   * Test a RegEx before using it. If there are any errors they will appear in the log file.
3. Enter the Date Format String in a .net format string.
4. If it is unable to get the specified field you can set up a Feedback Mode.

#### Modified Date

1. Determine the date you want to be used for page Modified.
   * Null (Left Blank)
   * Modified Date
   * Crawled Date
   * Meta Tags
   * RegEx
2. If you have selected Meta Tags or RegEx enter the name in Meta Tag/ Regex.
   * Test a RegEx before using it. If there are any errors they will appear in the log file.
3. Enter the Date Format String in a .net format string.
4. If it is unable to get the specified field you can set up a Feedback Mode.
5. Check Process Deletes to process deleted sites and pages during crawl.
6. Check Respect anchor titles for files to check for titles within files marked with anchors.
7. Uncheck Respect Robots to ignore a robot file and scan all pages.
   * If unchecked proceed with caution. Robot files are created for a reason.
8. Exclude text that appears between the A tags of a site by adding them to the Metadate field for link inner text box.
9. Exclude common link terms from your crawl by adding them to Link inner text to exclude field.
   * For Example Click Here, Download or Click the link

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-23 at 14.26.54.png" alt=""><figcaption></figcaption></figure>

#### Meta tag mappings

1. You can map the entity fields to meta tags from the web page.
   * Enter the full entity field in the left column. For example, entities.Websites.category.
   * Enter the meta tag name in the right column
2. You can map the metadata fields to meta tags from the web page.
   * Enter the full metadata field in the left column. For example, metadata.webtype.
   * Enter the meta tag name in the right column

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-23 at 14.28.38.png" alt=""><figcaption></figcaption></figure>
