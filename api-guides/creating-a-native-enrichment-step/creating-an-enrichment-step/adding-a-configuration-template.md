# Adding a Configuration Template

As you have seen, we can have step specific configuration, and in our test harness we set these parameters in code. However, when loaded into Aiimi Insight Engine we will want to configure the step via the Control Hub. To do this we create a template file that contains a segment of HTML that Control Hub uses to obtain the configuration parameters.

Create a file called helloworldes\_template.html in the class library project (the enrichment step project).

```
<div class="row">
    <div class="col-lg-8">
        <small>Text to append to the Text Content</small>
        <input name="helloWorldES_text" class="form-control" 
               [(ngModel)]="initialState.target.helloWorldES.text">
    </div>
</div>
```

Note the use of camel case to specify variable names.
