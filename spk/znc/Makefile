SPK_NAME = znc
SPK_VERS = 1.0
SPK_REV = 6
SPK_ICON = src/znc.png
DSM_UI_DIR = app
CHANGELOG = "1. Add modules colloquy and push"

DEPENDS = cross/busybox cross/$(SPK_NAME)

MAINTAINER = SynoCommunity
DESCRIPTION = Advanced IRC bouncer. An IRC bouncer is nothing more than an IRC proxy. ZNC will always be connected in your chat rooms, and will be the gateway between your clients, and your IRC servers. You can, for instance, consult messages while you were offline or hide your identity.
DESCRIPTION_FRE = Bouncer IRC avancé. Un bouncer IRC n\\\’est en fait qu\\\’un proxy IRC. ZNC restera connecté en permanence à vos salons de discussions et fera office de passerelle entre vos clients et vos serveurs IRC. Vous pourrez, par exemple, consultez des messages diffusés en votre absence ou masquer votre identité.
DESCRIPTION_SPN = IRC bouncer avanzado. Un IRC bouncer no es más que un proxy para IRC. ZNC estará siempre conectado a tus canales, y hará de puerta de enlace entre tus clientes y tus servidores IRC. Puedes, por ejemplo, consultar mensajes mientras estuviste desconectado o esconder tu identidad.
ADMIN_PORT = 8250
RELOAD_UI = yes
DISPLAY_NAME = ZNC

HOMEPAGE = http://wiki.znc.in/
LICENSE  =

WIZARDS_DIR = src/wizard/

INSTALLER_SCRIPT = src/installer.sh
SSS_SCRIPT       = src/dsm-control.sh
ADDITIONAL_SCRIPTS =

INSTALL_PREFIX = /usr/local/$(SPK_NAME)

POST_STRIP_TARGET = znc_extra_install

BUSYBOX_CONFIG = usrmng
ENV += BUSYBOX_CONFIG="$(BUSYBOX_CONFIG)"

include ../../mk/spksrc.spk.mk

.PHONY: znc_extra_install
znc_extra_install:
	install -m 755 -d $(STAGING_DIR)/var
	install -m 755 -d $(STAGING_DIR)/var/modules
	install -m 755 -d $(STAGING_DIR)/var/configs
	install -m 644 src/znc.conf $(STAGING_DIR)/var/configs/znc.conf
	install -m 755 -d $(STAGING_DIR)/app
	install -m 644 src/app/config $(STAGING_DIR)/app/config
	install -m 755 src/app/znc.cgi.pl $(STAGING_DIR)/app/znc.cgi
	install -m 755 -d $(STAGING_DIR)/app/images
	for size in 16 24 32 48; do \
		convert $(SPK_ICON) -thumbnail $${size}x$${size} \
		        $(STAGING_DIR)/app/images/$(SPK_NAME)-$${size}.png ; \
	done
