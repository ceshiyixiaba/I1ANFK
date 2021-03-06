---
production: &base
  #
  # 1. GitLab app settings
  # ==========================

  ## GitLab settings
  gitlab:
    ## Web server settings (note: host is the FQDN, do not include http://)
    host: localhost
    port: 80 # Set to 443 if using HTTPS, see installation.md#using-https for additional HTTPS configuration details
    https: false # Set to true if using HTTPS, see installation.md#using-https for additional HTTPS configuration details
    # The maximum time unicorn/puma can spend on the request. This needs to be smaller than the worker timeout.
    # Default is 95% of the worker timeout
    max_request_duration_seconds: 57

    # Uncomment this line below if your ssh host is different from HTTP/HTTPS one
    # (you'd obviously need to replace ssh.host_example.com with your own host).
    # Otherwise, ssh host will be set to the `host:` value above
    # ssh_host: ssh.host_example.com

    # Relative URL support
    # WARNING: We recommend using an FQDN to host GitLab in a root path instead
    # of using a relative URL.
    # Documentation: http://doc.gitlab.com/ce/install/relative_url.html
    # Uncomment and customize the following line to run in a non-root path
    #
    # relative_url_root: /gitlab

    # Content Security Policy
    # See https://guides.rubyonrails.org/security.html#content-security-policy
    content_security_policy:
      enabled: true
      report_only: false
      directives:
        base_uri:
        child_src:
        connect_src: "'self' http://localhost:* ws://localhost:* wss://localhost:*"
        default_src: "'self'"
        font_src:
        form_action:
        frame_ancestors: "'self'"
        frame_src: "'self' https://www.google.com/recaptcha/ https://www.recaptcha.net/ https://content.googleapis.com https://content-compute.googleapis.com https://content-cloudbilling.googleapis.com https://content-cloudresourcemanager.googleapis.com"
        img_src: "* data: blob:"
        manifest_src:
        media_src:
        object_src: "'none'"
        script_src: "'self' 'unsafe-eval' http://localhost:* https://www.google.com/recaptcha/ https://www.recaptcha.net/ https://www.gstatic.com/recaptcha/ https://apis.google.com"
        style_src: "'self' 'unsafe-inline'"
        worker_src: "'self' blob:"
        report_uri:

    # Trusted Proxies
    # Customize if you have GitLab behind a reverse proxy which is running on a different machine.
    # Add the IP address for your reverse proxy to the list, otherwise users will appear signed in from that address.
    trusted_proxies:
      # Examples:
      #- 192.168.1.0/24
      #- 192.168.2.1
      #- 2001:0db8::/32

    # Uncomment and customize if you can't use the default user to run GitLab (default: 'git')
    # user: git

    ## Date & Time settings
    # Uncomment and customize if you want to change the default time zone of GitLab application.
    # To see all available zones, run `bundle exec rake time:zones:all RAILS_ENV=production`
    # time_zone: 'UTC'

    ## Email settings
    # Uncomment and set to false if you need to disable email sending from GitLab (default: true)
    # email_enabled: true
    # Email address used in the "From" field in mails sent by GitLab
    email_from: example@example.com
    email_display_name: GitLab
    email_reply_to: noreply@example.com
    email_subject_suffix: ''
    email_smime:
      # Uncomment and set to true if you need to enable email S/MIME signing (default: false)
      # enabled: false
      # S/MIME private key file in PEM format, unencrypted
      # Default is '.gitlab_smime_key' relative to Rails.root (i.e. root of the GitLab app).
      # key_file: /home/git/gitlab/.gitlab_smime_key
      # S/MIME public certificate key in PEM format, will be attached to signed messages
      # Default is '.gitlab_smime_cert' relative to Rails.root (i.e. root of the GitLab app).
      # cert_file: /home/git/gitlab/.gitlab_smime_cert

    # Email server smtp settings are in config/initializers/smtp_settings.rb.sample

    # default_can_create_group: false  # default: true
    # username_changing_enabled: false # default: true - User can change their username/namespace
    ## Default theme ID
    ##   1 - Indigo
    ##   2 - Dark
    ##   3 - Light
    ##   4 - Blue
    ##   5 - Green
    ##   6 - Light Indigo
    ##   7 - Light Blue
    ##   8 - Light Green
    ##   9 - Red
    ##   10 - Light Red
    # default_theme: 1 # default: 1

    ## Automatic issue closing
    # If a commit message matches this regular expression, all issues referenced from the matched text will be closed.
    # This happens when the commit is pushed or merged into the default branch of a project.
    # When not specified the default issue_closing_pattern as specified below will be used.
    # Tip: you can test your closing pattern at http://rubular.com.
    # issue_closing_pattern: '\b((?:[Cc]los(?:e[sd]?|ing)|\b[Ff]ix(?:e[sd]|ing)?|\b[Rr]esolv(?:e[sd]?|ing)|\b[Ii]mplement(?:s|ed|ing)?)(:?) +(?:(?:issues? +)?%{issue_ref}(?:(?:, *| +and +)?)|([A-Z][A-Z0-9_]+-\d+))+)'

    ## Default project features settings
    default_projects_features:
      issues: true
      merge_requests: true
      wiki: true
      snippets: true
      builds: true
      container_registry: true

    ## Webhook settings
    # Number of seconds to wait for HTTP response after sending webhook HTTP POST request (default: 10)
    # webhook_timeout: 10

    ### GraphQL Settings
    # Tells the rails application how long it has to complete a GraphQL request.
    # We suggest this value to be higher than the database timeout value
    # and lower than the worker timeout set in unicorn/puma. (default: 30)
    # graphql_timeout: 30

    ## Repository downloads directory
    # When a user clicks e.g. 'Download zip' on a project, a temporary zip file is created in the following directory.
    # The default is 'shared/cache/archive/' relative to the root of the Rails app.
    # repository_downloads_path: shared/cache/archive/

    ## Impersonation settings
    impersonation_enabled: true

    ## Disable jQuery and CSS animations
    # disable_animations: true
---
