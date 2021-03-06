
# Best practices for developing Office Add-ins


Effective add-ins offer unique and compelling functionality that extends Office applications in a visually appealing way. To create a great add-in, provide an engaging first-time experience for your users, design a first-class UI experience, and optimize your add-in's performance. Apply the best practices described in this article to create add-ins that help your users complete their tasks quickly and efficiently.

## Provide clear value



- Create add-ins that help users complete tasks quickly and efficiently. Focus on scenarios that make sense for Office applications. For example:
 - Make core authoring tasks faster and easier, with fewer interruptions.
 - Enable new scenarios within Office.
 - Embed complementary services within Office hosts.
 - Improve the Office experience to enhance productivity.
- Make sure that the value of your add-in is clear to users right away by [creating an engaging first run experience](#create-an-engaging-first-run-experience).
- Create an [effective Office Store listing](http://msdn.microsoft.com/library/c66a6e6b-2e96-458f-8f8c-2a499fe942c9%28Office.15%29.aspx). Make the benefits of your add-in clear in your title and description. Don't rely on your brand to communicate what your add-in does.


## Create an engaging first-run experience



- Engage new users with a highly usable and intuitive first experience. Note that users are still deciding whether to use or abandon an add-in after they download it from the store.

 - Make the steps that the user needs to take to engage with your add-in clear. Use videos, placemats, paging panels, or other resources to entice users.

 - Reinforce the value proposition of your add-in on launch, rather than just asking users to sign in.

 - Provide teaching UI to guide users and make your UI personal.

    ![A screenshot that shows an add-in task pane with get started steps next to an add-in with no get started steps](../../images/586202ad-333b-417c-ad31-cc6eb952b239.png)

  - If your content add-in binds to data in the user's document, include sample data or a template to show users the data format to use.

    ![A screenshot that shows a content add-in with data next to a content add-in with no data](../../images/7de2215f-ccef-4f82-aa9d-babcbddae0c6.png)

- Offer [free trials](https://msdn.microsoft.com/en-us/library/dn456317.aspx#Anchor_1). If your add-in requires a subscription, make some functionality available without a subscription.

- Make signup simple. Prefill information (email, display name) and skip email verifications.

- Avoid pop ups. If you have to use them, guide the user to enable your pop up.

- Use [single sign-on (SSO) authentication](../outlook/authenticate-a-user-with-an-identity-token.md).

For templates that illustrate patterns that you can apply as you develop your first-run experience, see [UX design patterns for Office Add-ins](https://github.com/OfficeDev/Office-Add-in-UX-Design-Patterns-Code).

## Use add-in commands

- Provide relevant UI entry points for your add-in by using [add-in commands](../design/add-in-commands.md).

- Use commands to represent a specific action with a clear and specific outcome for users. Do not combine multiple actions in a single button.

- Provide granular actions that make common tasks within your add-in more efficient to perform. Minimize the number of steps an action takes to complete.

- For add-ins that extend the Office ribbon:
	- Place commands on an existing tab (Insert, Review, and so on) if the functionality provided fits there. For example, if your add-in enables users to insert media, add a group to the Insert tab. Note that not all tabs are available across all Office versions. For more information, see [Office Add-ins XML manifest](../overview/add-in-manifests.md). 
	- Place commands on the Home tab if the functionality doesn't fit on another tab, and you have fewer than six top-level commands. You can also add commands to the Home tab if your add-in needs to work across Office versions (such as Office Desktop and Office Online) and a tab is not available in all versions (for example, the Design tab doesn't exist in Office Online).  
	- Place commands on a custom tab if you have more than six top-level commands. 
  - Name your group to match the name of your add-in. If you have multiple groups, name each group based on the functionality that the commands in that group provide.
  - Do not add superfluous buttons to increase the real estate of your add-in.

     >**Note**  Add-ins that take up too much space might not pass [Office Store validation](https://msdn.microsoft.com/en-us/library/jj220035.aspx).

- For all icons:
	- Provide meaningful icons and [labels](http://msdn.microsoft.com/library/8cef4fce-e6a1-459b-951f-47ac03ec95a6%28Office.15%29.aspx) for buttons that clearly identify the action the user is taking.


 - Use PNG format with a transparent background.

 - Include [all eight supported sizes](https://msdn.microsoft.com/EN-US/library/mt267547.aspx#bk_resources). This creates the best experience for all supported resolutions.

  - Match the Office visual style. For example:

    - Keep your shapes simple and avoid multiple colors. Complex graphics are difficult to see at smaller sizes and resolutions.

    - Don't reuse visual metaphors for dissimilar commands. The same icon used for different actions will cause confusion.

    - Make your button labels clear and succinct. Use a combination of visual and textual information to convey meaning.

    - Test your icons in light and dark Office themes and high contrast settings. Note that icons might be difficult to see on dark backgrounds or in high contrast mode.

    - Use consistent icon sizes and positions to help with visual alignment on the ribbon.


    ![A screenshot that shows add-in command buttons that match the Office style next to buttons that don't match the style](../../images/31e11214-61e8-41c1-888c-29d167cb9486.png)


- Provide a version of your add-in that also works on hosts that do not support commands. A single add-in manifest can work in both command-aware (with commands) and non-command-aware (as a taskpane) hosts.

    ![A screenshot that shows a task pane add-in in Office 2013 and the same add-in using add-in commands in Office 2016](../../images/4f90a3cc-8cc4-4879-9a03-0bb2b6079026.png)



## Apply UX design principles



- Ensure that the look and feel and functionality of your add-in complements the Office experience. Use [Office UI Fabric](https://dev.office.com/fabric).

- Favor content over chrome. Avoid superfluous UI elements that don't add value to the user experience.

- Keep users in control. Ensure that users understand important decisions, and can easily reverse actions the add-in performs.

- Use branding to inspire trust and orient users. Do not use branding to overwhelm or advertise to users.

- Avoid scrolling. Optimize for 1366 x 768 resolution.

- Do not include unlicensed images.

- Use [clear and simple language](http://msdn.microsoft.com/library/8cef4fce-e6a1-459b-951f-47ac03ec95a6%28Office.15%29.aspx) in your add-in.

- Account for [accessibility](http://msdn.microsoft.com/library/3be1abbb-237a-48ec-8e17-72caa25a3cb2%28Office.15%29.aspx) - make your add-in easy for all users to interact with, and accommodate assistive technologies such as screen readers.

- Design for all platforms and input methods, including mouse/keyboard and [touch](#optimize-for-touch). Ensure that your UI is responsive to different form factors.

For templates that apply design principles that you can use and customize as you develop your add-in, see [UX design patterns for Office Add-ins](https://github.com/OfficeDev/Office-Add-in-UX-Design-Patterns-Code).

### Optimize for touch



- Use the [Context.touchEnabled](../../reference/shared/office.context.touchenabled.md) property to detect whether the host application your add-in runs on is touch enabled.

     >**Note**  This property is not supported in Outlook.
- Ensure that all controls are appropriately sized for touch interaction. For example, buttons have adequate touch targets, and input boxes are large enough for users to enter input.

- Do not rely on non-touch input methods like hover or right-click.

- Ensure that your add-in works in both portrait and landscape modes. Be aware that on touch devices, part of your add-in might be hidden by the soft keyboard.

- Test your add-in on a real device by using [sideloading](../testing/sideload-an-office-add-in-on-ipad-and-mac.md).


 >**Note**  If you're using [Office UI Fabric](https://github.com/OfficeDev/Office-UI-Fabric) for your design elements, many of these elements are taken care of.


## Optimize and monitor add-in performance



- Create the perception of fast UI responses. Your add-in should load in 500 ms or less.

- Ensure that all user interactions respond in under one second.

-  Provide loading indicators for long-running operations.

- Use a CDN to host images, resources, and common libraries. Load as much as you can from one place.

- Follow standard web practices to optimize your web page. In production, use only minified versions of libraries. Only load resources that you need, and optimize how resources are loaded.

- If operations take time to execute, provide feedback to users. Note the thresholds listed in the following table. See also [Resource limits and performance optimization for Office Add-ins](../../docs/develop/resource-limits-and-performance-optimization.md)


|**Interaction class**|**Target**|**Upper bound**|**Human perception**|
|:-----|:-----|:-----|:-----|
|Instant|<=50 ms|100 ms|No noticeable delay.|
|Fast|50-100 ms|200 ms|Minimally noticeable delay. No feedback necessary.|
|Typical|100-300 ms|500 ms|Quick, but too slow to be described as fast. No feedback necessary.|
|Responsive|300-500 ms|1 second|Not fast, but still feels responsive. No feedback necessary.|
|Continuous|>500 ms|5 seconds|Medium wait, no longer feels responsive. Might need feedback.|
|Captive|>500 ms|10 seconds|Long, but not long enough to do something else. Might need feedback.|
|Extended|>500 ms|>10 seconds|Long enough to do something else while waiting. Might need feedback.|
|Long running|>5 ms|>1 minute|Users will certainly do something else.|
- Monitor your service health, and use telemetry to monitor user success.


## Market your add-in



- Publish your add-in to the [Office Store](http://msdn.microsoft.com/library/ff075782-1303-4517-91cc-b3d730e9b9ae%28Office.15%29.aspx) and [promote it](http://msdn.microsoft.com/library/b19e21f8-76f5-44e1-9971-bef79cad4c71%28Office.15%29.aspx) from your website. Create an [effective Office Store listing](http://msdn.microsoft.com/library/c66a6e6b-2e96-458f-8f8c-2a499fe942c9%28Office.15%29.aspx).

- Use succinct and descriptive add-in titles. Include no more than 128 characters.

- Write short, compelling descriptions of your add-in. Answer the question "What problem does this add-in solve?".

- Convey the value proposition of your add-in in your title and description. Don't rely on your brand.

- Create a website to help users find and use your add-in.

