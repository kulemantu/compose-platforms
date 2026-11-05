# n8n pinned to an exact stable version, with `axios` made resolvable for the
# custom WhatsApp node (wa.dt.wrld packages/whatsapp-n8n-nodes). n8n 2.x no
# longer exposes axios to custom nodes, so `require("axios")` crashed n8n at
# startup and left it restarting in a loop for weeks.
#
# The link points at the axios n8n itself ships, so nothing extra is downloaded.
# If a future version drops it, the glob matches nothing and this build fails
# loudly, instead of the container crash-looping in production.
#
# To upgrade: change the tag and digest, and the image: tag in docker-compose.yml.
FROM n8nio/n8n:2.46.6@sha256:8602f5dfacbe2c931eeafd010de0e68182310e9f309921e780ab69182e92b3ae

USER root
RUN set -- /usr/local/lib/node_modules/n8n/node_modules/.pnpm/axios@*/node_modules/axios \
    && [ -e "$1" ] \
    && ln -s "$1" /usr/local/lib/node_modules/axios
USER node
