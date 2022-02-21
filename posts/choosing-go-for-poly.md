# Why I chose to write Poly in Go

When I talk about [Poly](https://github.com/TimothyStiles/poly) with other synthetic biologists the first thing they always want to know is why I chose to write Poly in Go. Why not Python, R, or something else?

I took great care in choosing the language given what Poly needed, and Python and R were so far away from meeting the requirements. It essentially came down to Go and Rust and Go won out on how easy it is to learn and all the amazing dev tools in its ecosystem.

## What were my requirements?

I wanted a to build library that was super stable with which I could build the next ten years of my life's work on. I wanted it to be widely adoptable, easy to use and maintain, and I wanted it to be fast and energy efficient i.e. scalable. At the time I imagined Poly would have an officially supported CLI so I also needed a language that shipped binaries to many different targets else I rely on my user's knowledge of Docker to run my code.

That binary requirement already ruled out Python, R, and Julia. Leaving me with just Go and Rust but even without that requirement I would have chosen Go. Remember, I was seeing this as infrastructure that needed to last ten years and Python et. al were never designed for this task.

Python was made as a scripting language. Something Guido van Rossum imagined as a way to write small scripts to automate tasks on his computer. It was never designed to build scalable, maintainable systems, and last I checked it still doesn't have native multi-threading which is needed to take advantage of the huge number of cores in modern CPUs. As far as I can tell people liked Python's syntax and that it wasn't C but could still theoretically run C and the rest is history. Python got user adoption, a package manager, and a bunch of web frameworks and general packages that made a developers life easy in the aughts but it's never been able to shake its original design intent as a scripting language. That's why almost every stable piece of Python code is essentially shipped with the operating system it was built on via Docker. That code won't run on your machine but the machine that it runs on will run on your machine.

R, Matlab, and probably to a lesser extent Julia suffer from similar problems that stem from their creator's design intent. All of these languages are meant to help people *prototype* things. They were never meant to help people *ship* infrastructure. In comes Go.

## Go was made to ship infrastructure

Sometime in the late aughts software engineering teams at Google were running into a problem. C was fast but a pain to develop in. Python was easier to develop in but it wasn't scalable enough for the massive infrastructure Google was running and maintaining day to day. Three highly qualified Google devs set out to create a language that was almost as fast a C and easier to develop in than Python that would allow thousands of Google employees to work on the same project in tandem with little issue. That's how Go was born.

From design intent you can already tell that Go was made to create stable, maintainable infrastructure and that its design intent closely aligns with my design intent for Poly. That same design intent is also why Docker, kubernetes, Git-LFS, Terraform, Ethereum, and countless projects have been written in Go. Go makes it easy to create massive, scalable projects with thousands of contributors.

## So what does Go do that Python doesn't?

* Statically typed language makes it harder to have implicit type errors.
* Native support for multi-threading and async processes.
* Easy to learn, simple syntax that makes it hard to be "clever".
* Compiles to binary executables.
* Simple package management based on Git repos.
* Native [example tests](https://go.dev/blog/examples). (This is my favorite feature to prevent doc rot)
* Native, centralized [doc sites](https://pkg.go.dev/github.com/TimothyStiles/poly) that automatically update with every release you push.
* 25X faster and more energy efficient than Python.
* Incredible tooling/CI/CD/Devops ecosystem.
* Incredible package ecosystem where most things actually run.
* A dev community that takes code quality seriously.
* No `pyenv`. I haven't managed individual dev environments for a project in YEARS. Go just works.
* Avoid Docker and just ship binaries via [GoReleaser](https://github.com/goreleaser/goreleaser/) unless you need a container for a horizontally scaling application or something.

## What does Python have that Go doesn't?

* A lot of scientists are familiar with it.
* Maybe better support for machine learning frameworks? Funny enough alot of the models trained with Python are exported and deployed with Go.
* Just-in-time compilation lets you do a whole bunch of cool, funky things that wouldn't be suitable for production code.

## Go was the easy choice

Looking at my criteria and Go's features it's now probably a little easier to see why I chose Go. I often get strange looks from synthetic biologists when I tell them I'm using Go but to be honest every backend engineer and web dev I've met is *thrilled* that I'm using Go over Python......

Happy hacking,

Tim
