# Mock Exam

Complete the following tasks, making a commit with a descriptive message for each task as you complete them.

> This exam is worth 100 points, but will **not** be counted towards your final grade.

## Tasks

1. Create a textarea field that allows a user to specify a message. Make sure to use the proper [Bootstrap classes for form inputs](https://getbootstrap.com/docs/3.3/css/#forms).
2. Create a "Send Message" button. Make sure to use the proper [Bootstrap classes for buttons](https://getbootstrap.com/docs/3.3/css/#buttons).
3. Disable the button if the user-specified message is empty.
4. Allow the user to click the button.
    - Upon clicking the button, you should trigger a "sendMessage" method on the Vue component.
    - The method should verify that the user-specified message is not empty. If it is empty, `return` immediately.
    - Make a POST request to our Slack Webhook URL (available in Canvas). Unlike our previous exercises with APIs, you will be *sending* data to the API as opposed to *retrieving* data.
        - Check out the documentation for [Vue Resource](https://github.com/pagekit/vue-resource/blob/develop/docs/http.md#example) to see how to send data in a POST request.
        - You can check the [Slack API Documentation](https://api.slack.com/incoming-webhooks) for details about what the POST request should contain.
        - Your goal is to see the message appear in the [#cis131 private group in our Slack team](https://otccis.slack.com/messages/G5TCCCGBT/).
        - When sending the user-specified message to the API, you should prepend it with "Adam says:", substituing my name with yours. This will allow everyone to know who said what!
    - Handle the API response accordingly.
        - As mentioned before, you are no looking for data to be returned to you in the response. You will only care about the status code.
        - If the status code is 200, your API call succeeded. Display a message to the user letting them know that it worked, and clear out your message input.
        - If the status code is *not* 200, then your API call failed. It is likely that you will encounter this early on in the project if you make any mistakes. You should present a message to the user letting them know that it failed, as well as information as to why the request failed. In the case of a failure, you *will* care about the response data, as it will tell you why the request failed. Again, refer to the Slack API Documentation for details about how error responses will look.
5. While the API call is executing, present the provided "Spinner" icon. Hide it after you have received your response from the API. It is very likely that it will take almost no time at all.
6. While the API call is executing, disable the "Send Message" button (as well as if the user-specified message is empty).

## Notes

- The user should be able to send as many messages as they'd like on the page without refreshing it.
- The user input should only be cleared after a *successful* API call.
- Vue Resource allows you to specify two callback functions when using the `then` method; the first is a "success" callback, and the second is an "error" callback. The error callback will be invoked (instead of the success callback) if the status code is not 200.
- Any inappropriate content sent into the Slack group will land you a zero, and you will be asked to leave the classroom.
- Any student-to-student communication during the exam will land you both a zero, and you will be asked to leave the classroom.
- Browsing the codebase on GitHub of a fellow classmate during the exam will land you a zero, and you will be asked to leave the classroom.
- You *may* access any of your personal repositories on GitHub.
- You *should* access documentation for Bootstrap, Vue, Vue Resource, Slack, etc.

## Handy Links

- Study Guide: https://github.com/OTCCIS131/study-guide
- Slack API Documentation: https://api.slack.com/incoming-webhooks
- Vue Resource Documentation: https://github.com/pagekit/vue-resource/blob/develop/docs/http.md#example