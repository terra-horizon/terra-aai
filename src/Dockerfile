FROM quay.io/keycloak/keycloak:26.4.7

USER root

COPY terra-theme /opt/keycloak/themes/terra-theme

RUN chown -R keycloak:0 /opt/keycloak/themes/terra-theme

USER keycloak

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
