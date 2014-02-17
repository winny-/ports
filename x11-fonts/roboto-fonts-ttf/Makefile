# Created by: Winston Weinert <winstonw@lavabit.com>
# $FreeBSD: head/x11-fonts/roboto-fonts-ttf/Makefile 340722 2014-01-22 17:00:46Z mat $

PORTNAME=	roboto-fonts-ttf
PORTVERSION=	1.2
PORTEPOCH=	1
CATEGORIES=	x11-fonts
MASTER_SITES=	http://developer.android.com/downloads/design/
DISTNAME=	roboto-${PORTVERSION}

MAINTAINER=	winston@ml1.net
COMMENT=	The Roboto typeface family

LICENSE=	APACHE20

BUILD_DEPENDS=	mkfontdir:${PORTSDIR}/x11-fonts/mkfontdir \
		mkfontscale:${PORTSDIR}/x11-fonts/mkfontscale

USE_ZIP=	yes
WRKSRC=		${WRKDIR}/Roboto_v${PORTVERSION}

FONTDIR=	lib/X11/fonts/Roboto
PKGMESSAGE=	${WRKDIR}/pkg-message
PLIST_SUB=	FONTDIR=${FONTDIR}
SUB_FILES=	pkg-message
SUB_LIST=	FONTDIR=${FONTDIR}

NO_STAGE=	yes
do-build:
	@cd ${WRKSRC}/ && \
		${LOCALBASE}/bin/mkfontscale && \
		${LOCALBASE}/bin/mkfontdir

do-install:
	${MKDIR} ${PREFIX}/${FONTDIR}/
	cd ${WRKSRC}/Roboto && ${INSTALL_DATA} *.ttf ${PREFIX}/${FONTDIR}/
	cd ${WRKSRC}/RobotoCondensed && ${INSTALL_DATA} *.ttf ${PREFIX}/${FONTDIR}/

post-install:
	@${CAT} ${PKGMESSAGE}

.include <bsd.port.mk>
