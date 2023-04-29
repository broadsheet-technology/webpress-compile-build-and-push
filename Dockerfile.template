FROM ghcr.io/broadsheet-technology/webpress-compile:latest as compiled-theme
WORKDIR /app
COPY . .

RUN /app/compile.sh

FROM ghcr.io/broadsheet-technology/wordpress:0.5

COPY --from=compiled-theme /app/dist/wp-content/themes/. /srv/themes/.
RUN chown -R www-data:www-data /srv/themes
RUN chmod -R 755 /srv/themes

COPY --from=compiled-theme /app/dist/stencil-stats.json /srv/stencil-stats.json
RUN chown -R www-data:www-data /srv/stencil-stats.json
RUN chmod -R 755 /srv/stencil-stats.json