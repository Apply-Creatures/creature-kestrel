<!-- PROJECT SHIELDS -->
[![Codacy Badge][codacy-shield]][codacy-url]
[![Issues][issues-shield]][issues-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![repo-size][repo-size-shield]][repo-size-url]
[![Contributors][contributors-shield]][contributors-url]
[![license][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

  <h3 align="center">kestrel</h3>

   <a href="#">
      <img src="images/kestrel.png" alt="screenshot">
   </a>

  <p align="center">
    An open-source project tracker system designed to enhance organization and tracking.
    <br />
    <a href="#"><strong>See live (soon) »</strong></a>
    <br />
    <br />
    <a href="https://github.com/apply-creatures/creature-kestrel/issues">Report Bug</a>
    ::
    <a href="https://github.com/apply-creatures/creature-kestrel/issues">Request Feature</a>
  </p>
</div>

<p align="center">
OK, DOkey
</p>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
      <ol>
         <li>
            <a href="#about">About</a>
            <ul>
                <li>
                    <a href="#built-with">Built With</a>
                </li>
            </ul>
         </li>
         <li>
         <a href="#getting-started">Getting Started</a>
         <ul>
            <li><a href="#prerequisites">Prerequisites</a></li>
            <li><a href="#repo">Repo</a></li>
            <li><a href="#develop">Develop</a></li>
            <li><a href="#build">Build</a></li>
            <li><a href="#deploy">Deploy</a></li>
         </ul>
         </li>
         <li><a href="#roadmap">Roadmap</a></li>
         <li><a href="#contributing">Contributing</a></li>
         <li><a href="#license">License</a></li>
         <li><a href="#acknowledgments">Acknowledgments</a></li>
      </ol>
</details>

<hr/>

**TL;DR** - skip to [getting-started](#getting-started)

<hr/>

<!-- ABOUT THE PROJECT -->

## About

Lost in a mess of Docs? Never quite sure who has access? Colleagues requesting the same information repeatedly in chat? It’s time to get your team’s knowledge organized.

## Features

* **Intuitive editing experience** - A blazing fast editor with markdown support, slash commands, interactive embeds, and more
* **Cycles**: Keep up your team's momentum with Cycles. Gain insights into your project's progress with burndown charts and other valuable features.
* **Collab**: Collaborate with team mates on documents in realtime. Comments & threads keep conversations organized.
* **Markdown**: Everything markdown

Of course, nothing is perfect, but I will try to keep this up to date and fix issues right here.
If you've truly tried everything and still can't get this to work for you, try to reach out. Or raise an issue. But I make no promise.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

- [Outline](https://getoutline.com/) - Knowledge tracking platform
- [Docker](https://www.docker.com/) - Containerization platform
- [Fly.io](https://fly.io/) - Deployment platform

### Also using

- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Node.js](https://nodejs.org/)

<hr/>

<!-- GETTING STARTED -->

## Getting Started

### Prerequisites

- You need [Git](https://git-scm.com/) installed
- And [Docker](https://www.docker.com/)
- Fly.io account and CLI to deploy onto Fly 

### Set up repo

```bash
$ git clone https://github.com/apply-creatures/creature-kestrel.git
$ cd ./creature-kestrel
```

### Develop

If you are a developer, you may know you are doing. so

1. Set up redis
2. Setup postgres
3. Have docker running

Check the env variables throughout the deploy section and figure it out.

## Deploy

### Setup datastores

Well we need a bunch, redis, postgres, and some s3 compatible object storage (tigris will do).

1. Setup Redis

Either have your own redis running, or follow these to setup on fly.io

   ```bash
   fly redis create
   ```

2. **setup postgres

As before, either you have one or go create one.
Either way you need to create a db called:

- `kestrel`

### Deploy component


1. **Deploy the API:**

   ```bash
   cd ./outline
   ```

2. **Build and deploy:**

   ```bash
   fly deploy # you may need to launch if that's the first time
   ```

3. **Set env variables and secrets**

Set the environment variables with the values provided after bucket creation:

```bash
fly secrets set POSTGRES_HOST=thehost # optional, see the one after that
fly secrets set DATABASE_URL=postgres://postgres:password@domain:5432
fly secrets set REDIS_HOST=cluster.upstash.io
fly secrets set REDIS_URL=redis://default:cluster@sub.upstash.io:6379
fly secrets set CORS_ALLOWED_ORIGINS="https:/example.com" # you better set your own there
```

## Usage

After deployment, you can access via a web browser

## Acknowledgments

- [Docker](https://www.docker.com/)
- [Fly.io](https://fly.io/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<hr/>

## Roadmap

- [x] Setup a repo with initial configurations
- [x] Setup Dockkerfiles
- [x] Test features
- [ ] Set up email
- [ ] CI pipeline

<hr/>

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/some-feature`)
3. Commit your Changes (`git commit -m 'Add some feature'`)
4. Push to the Branch (`git push origin feature/some-feature`)
5. Open a Pull Request

<hr/>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<hr/>

## Acknowledgments

It would never end. I've done this work not just off dozens of other people's open source work, but hundreds, thousands, or maybe millions.

<!-- Refs -->

[codacy-url]: https://app.codacy.com/gh/apply-creatures/creature-kestrel/dashboard
[codacy-shield]: https://img.shields.io/codacy/grade/appid?style=for-the-badge
[contributors-shield]: https://img.shields.io/github/contributors/apply-creatures/creature-kestrel.svg?style=for-the-badge
[contributors-url]: https://github.com/apply-creatures/creature-kestrel/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/apply-creatures/creature-kestrel.svg?style=for-the-badge
[forks-url]: https://github.com/apply-creatures/creature-kestrel/network/members
[stars-shield]: https://img.shields.io/github/stars/apply-creatures/creature-kestrel.svg?style=for-the-badge
[stars-url]: https://github.com/apply-creatures/creature-kestrel/stargazers
[issues-shield]: https://img.shields.io/github/issues/apply-creatures/creature-kestrel.svg?style=for-the-badge
[issues-url]: https://github.com/apply-creatures/creature-kestrel/issues
[license-shield]: https://img.shields.io/github/license/apply-creatures/creature-kestrel.svg?style=for-the-badge
[license-url]: https://github.com/apply-creatures/creature-kestrel/blob/main/LICENSE
[score-shield]: https://img.shields.io/ossf-scorecard/github.com/apply-creatures/creature-kestrel?style=for-the-badge
[score-url]: https://github.com/apply-creatures/creature-kestrel
[repo-size-shield]: https://img.shields.io/github/repo-size/apply-creatures/creature-kestrel?style=for-the-badge
[repo-size-url]: https://github.com/apply-creatures/creature-kestrel/archive/refs/heads/main.zip
[product-screenshot]: images/kestrel.png


## Changelog

Changelog see [here](CHANGELOG.md)

## License

[![license][license-shield]][license-url].

Beware that the [outline](https://www.getoutline.com/) application is licensed as BSL.

If you too produce work and publish it out there, it's clearer to choose a [license](https://choosealicense.com).