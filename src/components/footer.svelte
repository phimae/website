<script>
  const socialLinks = [
    {
      href: "https://twitter.com/gitpod",
      alt: "Twitter",
      icon: "/svg/brands/twitter.svg",
      trackingName: "twitter",
    },
    {
      href: "https://github.com/gitpod-io",
      alt: "GitHub",
      icon: "/svg/brands/github.svg",
      trackingName: "github",
    },
    {
      href: "https://community.gitpod.io/",
      alt: "Discourse",
      icon: "/svg/brands/discourse.svg",
      trackingName: "discourse",
    },
    {
      href: "https://www.gitpod.io/chat",
      alt: "Discord",
      icon: "/svg/brands/discord.svg",
      trackingName: "discord",
    },
  ];
</script>

<style type="text/postcss">
  a {
    @apply text-dark-grey no-underline;
  }

  a:hover,
  a:focus {
      @apply text-black;
    }

  footer {
    @media (min-width: 56.25rem) {
      max-width: 56.25rem;
    }
  }

  ul {
    @media (max-width: 768px) {
      @apply mb-xx-small;
    }

    @media (max-width: 500px) {
      flex: 0 0 34%;
    }
  }

  li:first-child {
      @apply font-semibold text-black;
    }

    li:not(:last-of-type) {
      @apply mb-macro;
    }

  .footer__bottom {
    @media (max-width: 340px) {
      @apply flex-col-reverse items-center;
    }
  }

  .footer__copy {
    @media (max-width: 340px) {
      margin-top: var(--micro);
    }
  }

  .footer__social-link:not(:last-child) {
    @apply mr-micro;
  }
  .footer__social-link:hover {
    background: #ffffff;
    opacity: 0.8;
  }
</style>

<div class="pb-8 bg-gray-100 text-p-footer" data-id="footer">
  <footer
    class="footer py-large m-auto px-xx-small md:max-w-3xl md:py-small md:px-xx-small"
  >
    <div class="flex justify-between flex-wrap pb-micro md:pb-small">
      <ul>
        <li>Gitpod</li>
        <li><a href="/">Home</a></li>
        <li><a href="/features">Features</a></li>
        <li><a href="/pricing">Pricing</a></li>
        <li><a href="/changelog">Changelog</a></li>
        <li><a href="/self-hosted">Self-Hosted</a></li>
        <li>
          <a href="/gitpod-vs-github-codespaces"
            >Gitpod vs GitHub <br />Codespaces
          </a>
        </li>
        <li>
          <a
            href="https://www.gitpodstatus.com/"
            target="_blank"
            on:click={() =>
              window.analytics.track("external_resource_clicked", {
                context: "footer",
                name: "status",
                url: "https://www.gitpodstatus.com/",
              })}
            rel="noopener">Status</a
          >
        </li>
      </ul>
      <ul>
        <li>Developer</li>
        <li><a href="/#get-started">Getting started</a></li>
        <li><a href="/screencasts">Screencasts</a></li>
        <li><a href="/blog">Blog</a></li>
        <li><a href="/docs">Documentation</a></li>
        <li><a href="/support">Support</a></li>
        <!-- <li><a href="/guides">Guides</a></li> -->
        <li>
          <a
            href="https://github.com/gitpod-io/gitpod/issues/new?template=bug_report.md"
            target="_blank"
            rel="noopener"
            on:click={() =>
              window.analytics.track("external_resource_clicked", {
                context: "footer",
                name: "bug-report",
                url:
                  "https://github.com/gitpod-io/gitpod/issues/new?template=bug_report.md",
              })}>Report a bug</a
          >
        </li>
        <li>
          <a
            href="https://community.gitpod.io"
            target="_blank"
            rel="noopener"
            on:click={() =>
              window.analytics.track("social_opened", {
                context: "footer",
                platform: "discourse",
              })}>Community</a
          >
        </li>
      </ul>
      <ul>
        <li>Company</li>
        <li><a href="/about">About</a></li>
        <li>
          <a href="/careers" class="highlighted">Careers</a>
        </li>
        <li><a href="/contact">Contact</a></li>
        <li><a href="/media-kit">Media Kit</a></li>
      </ul>
      <ul>
        <li>Legal</li>
        <li><a href="/imprint">Imprint</a></li>
        <li>
          <a href="/terms">Terms of Service</a>
        </li>
        <li>
          <a href="/privacy">Privacy Policy</a>
        </li>
      </ul>
    </div>

    <div
      class="footer__bottom flex justify-between border-t border-solid border-sand-dark pt-xx-small md:pt-x-small"
    >
      <div class="footer__copy flex items-center">
        <a href="/"
          ><div class="relative -top-px z-0">
            <img
              src="/svg/logo-textless.svg"
              alt="Gitpod"
              height="24"
              width="24"
            />
          </div></a
        ><span class="ml-macro"
          >Copyright &copy; {new Date().getFullYear()} Gitpod</span
        >
      </div>
      <div class="flex">
        {#each socialLinks as link}
          <a
            href={link.href}
            target="_blank"
            on:click={() =>
              window.analytics.track("social_opened", {
                context: "footer-logo",
                platform: link.trackingName,
              })}
            class="footer__social-link"
          >
            <img src={link.icon} alt={link.alt} height="24" width="24" />
          </a>
        {/each}
      </div>
    </div>
  </footer>
</div>
