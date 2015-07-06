# Building and Deploying Your Project
Now that we have a project created and we've made some changes to customize it, we now need a method of deploying that project. The process of preparing ("building") your project for deployment and then actually deploying it is the final step toward making your project available to users on the web. 

There was a time when web projects often separated what were known as System Admin (sysadmin) or System Operator (sysop) duties and developer duties. The admins and ops would make sure servers were running, properly configured, and properly connected into the network. The system of servers, routers, switches and other hardware that keeps any given network center operational is known as the "network infrastructure". When companies bought servers and put them in specially designed rooms connected to lots of other equipment, it was necessary to have teams of people managing that equipment.

These days, most companies do not own their own network hardware. As the needs of websites have become both more diverse and more standardized, it is easier and easier to leverage third party solutions to keep a website or application running. Physical hosting of servers in a Network Operation Center (NOC) has given way to cloud-based hosting of virtual servers. 

This evolution has transformed the way developers interact with their work. We are in the midst of the "devops" era. Devops is a term that combines development of a project (website or application) and the management of how that project is deployed and served to users. Since the optimization and securing of any project so often depends on specific details of the project, it makes sense that these two sets of tasks would come together. However, the process of building and deploying sites is still time consuming and warrants some consideration.

## Tools for the Job
As with everything in web development, we begin our work here by choosing the tool we will use to help us achieve our goals. In this case, the goal is to build and deploy our static website to the Github Pages static website server. This service is free and easy to use, so it's great for our work here. You should be able to use this same approach with many other hosting solutions by modifying some of these details.

To manage bringing together all of the pieces, we will use Grunt. Grunt is a default component in the webapp generator (and the AngularJS app generator we will use later), so it is easy to set up and work with in our project. (It's worth noting, as we have earlier in this book, that Gulp is a viable alternative to Grunt. Although the specific details of implementing Gulp are quite different from implementing Grunt, the general concepts and approach here can be done with Gulp.)

Our project came with almost all of the smaller components Grunt needs to handle the "build" part of our "build and deploy" process. It is already building your site for preview when you alter files and preview them on your local development server. It is processing your SCSS into CSS using `node-sass`, and it is using a variety of tools to minify, compress, optimize and otherwise make your site happen. The good news is that we do not have to alter these processes at all, but as we work through setting up Grunt to handle our deployments we'll take a look at how all of these things are configured, too.

## Grunt Build Control
The one thing our Grunt setup is missing out of the box is a way to actually deploy the built files to a server. In order to make this happen, we will use a component called `grunt-build-control` ([Github repo](https://github.com/robwierzbowski/grunt-build-control)). We will configure this component in our `Gruntfile.js` so it builds our project to a `gh-pages` branch, which Github will then automatically pick up and publish for us.

This will allow us to run a single command to publish our site, like this:

```bash
grunt buildcontrol
```

Of course, this will require a little effort to set up. In this chapter we will work through the process of adding `grunt-build-control` to our project. We will explore how to use `npm` to add local modules specific to our projects, and we will look at how the `Gruntfile.js` works to configure `grunt` tasks. Finally, we will publish the experimental project we've been working on to Github Pages and verify it is available to the public.