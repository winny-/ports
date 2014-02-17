# Created by: Winston Weinert <winstonw@lavabit.com>
# $FreeBSD: head/net/drawterm/Makefile 340722 2014-01-22 17:00:46Z mat $

PORTNAME=	drawterm
PORTVERSION=	20140106
CATEGORIES=	net
MASTER_SITES=	http://swtch.com/drawterm/
EXTRACT_SUFX=	.tgz

MAINTAINER=	winston@ml1.net
COMMENT=	Plan9 cpu client

# Additionally the Lucent Public License
LICENSE=	MIT

USE_XORG=	x11 xt

PLIST_FILES=	bin/drawterm
PORTDOCS=	LICENSE README
WRKSRC=		${WRKDIR}/${PORTNAME}

MAKE_ARGS=	CONF=pthread

NO_STAGE=	yes
do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/drawterm ${PREFIX}/bin

post-install:
.if !defined(NOPORTDOCS)
	${MKDIR} ${DOCSDIR}
	${INSTALL_MAN} ${WRKSRC}/README ${WRKSRC}/LICENSE ${DOCSDIR}
.endif

.include <bsd.port.mk>
