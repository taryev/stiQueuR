![](stiqueur.svg)  
stiQueuR pronounced `\sti.kœʁ\ ` (oui oui baguette :baguette_bread: :fr:) manages the link of [qr.taryev.fr](https://qr.taryev.fr) 
(QR code sticker on my laptop).

## Usage
Edit `link.txt` then commit & push to main.
To avoid errors, the link must be double-quoted.  
A GitHub action will update the subdomain's [Caddy](https://github.com/caddyserver/caddy) configuration.

## Configuration  
Edit/add repository secrets in repo's actions secret and variables settings.

- `HOST`, `PORT`, `USER`, `KEY` : credentials to establish SSH connection to server,
- `CADDYENDOINT` : path to [Caddy API](https://caddyserver.com/docs/api) endpoint [^1].

### Example Caddy configuration
#### CaddyFile configuration example
```
qr.acme.web {
    redir https://www.youtube.com/watch?v=dQw4w9WgXcQ
}
```
#### JSON Caddy configuration
If you don't use CaddyFiles you probably know how to edit a Caddy JSON config file to handle a route with a Location header and a 302 status code :rocket:.

[^1] To get your full endpoint path, you have to read the JSON version of your Caddy config file using `$ curl localhost:2019/config/ | jq`
