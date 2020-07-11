**Git-flow**

Git-flow was described by Vincent Driessen on his 2010 post A successful Git branching model. I&#39;ve found it to be a great way to organize a repository. In short, you:

Keep your master branch as the code that has been released,

Use a develop branch as the current &quot;snapshot&quot; of what will go into the next release - your living beta,

Spawn off feature branches off develop for every new feature, which are merged back into it when they&#39;re ready,

When you are ready to release, you merge to master and tag with a release version.

There are other considerations for how to deal with hotfixes, but that&#39;s the gist of it. You can see a git-flow diagram below:

This is a great approach and it has several advantages:

master always remains as a stable reflection of your live code,

You can trivially do hotfixes without worrying about unfinished features,

Feature branches ensure that teams working in parallel don&#39;t trip over each other and that conflicts need to be handled only once (the moment the feature is done),

It allows teams to cherry-pick changes other teams may be doing on their feature branches, without needing these commits to be on develop already,

It lets you do a release off develop at any point - if a feature isn&#39;t ready, that&#39;s OK, you just leave it for the next release.

There are helper scripts to assist you with Gitflow. Atlassian&#39;s SourceTree supports it directly as well.

**Github-flow**

Proponents of Github-flow (and its cousin Gitlab-flow) have a few complaints about it. The main argument is that it goes against continuous delivery, since at some point someone needs to &quot;flip a switch&quot; and do a release from develop into master.

That&#39;s a valid argument. Nothing is less continuous than manual switch-flipping.

The Github-flow proposal is that you should:

Do away with the develop branch altogether,

Spawn all feature branches off master, and merge them back into master when ready,

Version tagging should not be carried by a human, but by an automated process whenever code is pushed to live,

These are valid points and they do result on a lighter-weight workflow. But they ignore that there are cases where you want a manual release, a negotiation of what is supposed to go into any particular version.

**Git and GitHub with Briana Swift**

**Git &amp; GitHub: GitHub Workflow**

- Branch
- Commit
- Pull Request
- Commit
- Merge

**Git &amp; GitHub: Working Locally**

**git clone**

- copies repo
- All branches
- All history

**git remote-v**

- origin al remote
- other remotes
- forks
- upstream

**Git &amp; GitHub: Git Status**

- Head pointer
- Working directory
- Stanging area
- Compare

Remote tracking

Branch

- Suggestions

**Git &amp; GitHub: Saved Changes**

\*Working staging .git directory

git add git commit git log

git dıff

**Git &amp; GitHub: Git Pull &amp; Git Push**

git pull

- update local
- git fetch
- git merge

git push

- update remote
- current branch

**Git &amp; GitHub: Git Reset**

- git reset-soft
- git reset
- git reset--hard

**Git &amp; GitHub: Merge Strategies**

Fast Forward Merge

- Rebase
- No new commits on master
- No merge commit
- Linear History

Recursive Merge

- no-ff
- New commits
- Merge commit created
- Commit -2 parent

**Git &amp; GitHub: Organization and Teams**

**Git &amp; GitHub: Migrate to Github**

- Code
- History
- Integration
- QA process
- Code review

KEEP \&lt;----- ? ------\&gt; CHANGE

**Git &amp; GitHub: Integrations**

Project Management

Monitoring C.I.

Deploy

**Git &amp; GitHub: Changing History**

Parent/Child

Safe

- git revert

Possibly Dangerous

- git reset
- git rebase
- git commit --amend
- git cherry-pick

**Merge a pull request**

When the desired number of reviewers have approved a pull request, you can merge the pull request if you have write (or admin) permission on the repository. If you&#39;ve been touching the same code as someone else, you may have [a merge conflict that you need to resolve locally](https://confluence.atlassian.com/bitbucket/resolve-merge-conflicts-704414003.html). After you merge a pull request, you can revert the pull request to remove the merge commit from the repository.

- **Merge commit** —Keeps all commits from your source branch and makes them part of the destination branch.
This option is the same as entering git merge --no-ff in the command line.
- **Squash** —Combines your commits when you merge the source branch into the destination branch.
This option is the same as entering git merge --squash in the command line.
- **Fast forward** —Moves commits from the source branch to the destination branch (if the destination has no new commits).
This option is the same as entering git merge --ff-only in the command line.

**What is the ASP.NET Boilerplate?**

ASP.NET Boilerplate (ABP) is an [open source](https://github.com/aspnetboilerplate/aspnetboilerplate) and well-documented application framework. It&#39;s not just a framework, it also provides a strong [architectural model](https://aspnetboilerplate.com/Pages/Documents/NLayer-Architecture) based on Domain Driven Design, with all the best practices in mind.

ABP works with the latest ASP.NET Core &amp; EF Core but also supports ASP.NET MVC 5.x &amp; EF 6.x as well.

Let&#39;s see some of ABP&#39;s benefits here:

- [Dependency Injection](https://aspnetboilerplate.com/Pages/Documents/Dependency-Injection): ABP uses and provides a conventional DI infrastructure. Since this class is an application service, it&#39;s conventionally registered to the DI container as transient (created per request). It can simply inject any dependencies (such as the IRepository\&lt;Task\&gt; in this sample).
- [Repository](https://aspnetboilerplate.com/Pages/Documents/Repositories): ABP can create a default repository for each entity (such as IRepository\&lt;Task\&gt; in this example). The default repository has many useful methods such as the FirstOrDefault method used in this example. We can extend the default repository to suit our needs. Repositories abstract the DBMS and ORMs and simplify the data access logic.
- [Authorization](https://aspnetboilerplate.com/Pages/Documents/Authorization): ABP can check permissions declaratively. It prevents access to the UpdateTask method if the current user has no &quot;update tasks&quot; permission or is not logged in. ABP not only uses declarative attributes, but it also has additional ways in which you can authorize.
- [Validation](https://aspnetboilerplate.com/Pages/Documents/Validating-Data-Transfer-Objects): ABP automatically checks if the input is null. It also validates all the properties of an input based on standard data annotation attributes and custom validation rules. If a request is not valid, it throws a proper validation exception and handles it in the client side.
- [Audit Logging](https://aspnetboilerplate.com/Pages/Documents/Audit-Logging) : User, browser, IP address, calling service, method, parameters, calling time, execution duration and some other information is automatically saved for each request based on conventions and configurations.
- [Unit Of Work](https://aspnetboilerplate.com/Pages/Documents/Unit-Of-Work): In ABP, each application service method is assumed to be a unit of work by default. It automatically creates a connection and begins a transaction at the beginning of the method. If the method successfully completes without an exception, then the transaction is committed and the connection is disposed. Even if this method uses different repositories or methods, all of them will be atomic (transactional). All changes on entities are automatically saved when a transaction is committed. We don&#39;t even need to call the \_repository.Update(task) method as shown above.
- [Exception Handling](https://aspnetboilerplate.com/Pages/Documents/Handling-Exceptions): We almost never have to manually handle exceptions in ABP on a web application. All exceptions are automatically handled by default! If an exception occurs, ABP automatically logs it and returns a proper result to the client. For example, if this is an AJAX request, it returns a JSON object to the client indicating that an error occurred. It hides the actual exception from the client unless the exception is a UserFriendlyException, as used in this sample. It also understands and handles errors on the client side and show appropriate messages to the users.
- [Logging](https://aspnetboilerplate.com/Pages/Documents/Logging): As you see, we can write logs using the Logger object defined in the base class. Log4Net is used by default, but it&#39;s changeable and configurable.
- [Localization](https://aspnetboilerplate.com/Pages/Documents/Localization): Note that we used the &#39;L&#39; method while throwing the exception? This way, it&#39;s automatically localized based on the current user&#39;s culture. See the [localization](https://aspnetboilerplate.com/Pages/Documents/Localization) document for more.
- [Auto Mapping](https://aspnetboilerplate.com/Pages/Documents/Data-Transfer-Objects): In the last line, we map input using the MapTo method of ABP&#39;s IObjectMapper. properties to entity properties. It uses the AutoMapper library to perform the mapping. We can easily map properties from one object to another based on naming conventions.
- [Dynamic API Layer](https://aspnetboilerplate.com/Pages/Documents/Dynamic-Web-API): TaskAppService is a simple class, actually. We generally have to write a wrapper API Controller to expose methods to JavaScript clients, but ABP automatically does that on runtime. This way, we can use application service methods directly from clients.
- [Dynamic JavaScript AJAX Proxy](https://aspnetboilerplate.com/Pages/Documents/Dynamic-Web-API#dynamic-javascript-proxies) : ABP creates proxy methods that make calling application service methods as simple as calling JavaScript methods on the client.
