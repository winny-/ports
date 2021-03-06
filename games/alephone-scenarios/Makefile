# New ports collection makefile for:	alephone-scenarios
# Date created:				2007-03-06
# Whom:					alepulver
#
# $FreeBSD: ports/games/alephone-scenarios/Makefile,v 1.8 2011/09/18 18:43:29 pawel Exp $
#

PORTNAME=	scenarios
PORTVERSION=	1.0
PORTREVISION=	6
CATEGORIES=	games
MASTER_SITES=	http://files3.bungie.org/trilogy/:bungie \
		http://files5.bungie.org/marathon/:rubicon \
		http://nardofiles.bungie.org/:nardofiles \
		http://eternal.bungie.org/files/_releases/:eternal \
		SF/../emr3:emr \
		http://ryoko.treellama.org/:gray \
		http://www.simplici7y.com/version/file/783/:phoenix
PKGNAMEPREFIX=	alephone-
DISTFILES=	#
DIST_SUBDIR=	alephone
EXTRACT_ONLY=	#

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Free scenarios for the Aleph One engine

RUN_DEPENDS=	alephone:${PORTSDIR}/games/alephone

USE_ZIP=	yes
NO_BUILD=	yes
NO_WRKSUBDIR=	yes

OPTIONS=	EMR "Install Excalibur: Morgana's Revenge data" off \
		ETERNAL "Install Eternal X data" off \
		EVIL "Install Marathon Evil data" on \
		RED "Install Marathon Red data" on \
		RUBICON "Install Rubicon X data" off \
		TI "Install Tempus Irae data" off \
		GRAY "Install The Gray Incident data" off \
		PHOENIX "Install Marathon Phoenix data" off

SUB_FILES=	wrapper

.include <bsd.port.pre.mk>

DATADIR!=	cd ${PORTSDIR}/games/alephone && ${MAKE} -V DATADIR

.if defined(WITH_EMR)
FETCH_ARGS=	-Fpr
EMR_FILE=	emr-3.0-0602.tgz
DISTFILES+=	${EMR_FILE}:emr
PLIST_SUB+=	EMR=""
AO_PACKS+=	emr
DESKTOP_ENTRIES+="Excalibur: Morgana's Revenge" "" "" "alephone-emr" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	EMR="@comment "
.endif

.if defined(WITH_ETERNAL)
DISTFILES+=	EternalXv103Full${EXTRACT_SUFX}:eternal
EXTRACT_ONLY+=	EternalXv103Full${EXTRACT_SUFX}
PLIST_SUB+=	ETERNAL=""
AO_PACKS+=	eternal
DESKTOP_ENTRIES+="Eternal X" "" "" "alephone-eternal" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	ETERNAL="@comment "
.endif

.if !defined(WITHOUT_EVIL)
DISTFILES+=	MarathonEvil${EXTRACT_SUFX}:bungie
EXTRACT_ONLY+=	MarathonEvil${EXTRACT_SUFX}
PLIST_SUB+=	EVIL=""
AO_PACKS+=	evil
DESKTOP_ENTRIES+="Evil" "" "" "alephone-evil" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	EVIL="@comment "
.endif

.if !defined(WITHOUT_RED)
DISTFILES+=	MarathonRED${EXTRACT_SUFX}:bungie
EXTRACT_ONLY+=	MarathonRED${EXTRACT_SUFX}
PLIST_SUB+=	RED=""
AO_PACKS+=	red
DESKTOP_ENTRIES+="Marathon Red" "" "" "alephone-red" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	RED="@comment "
.endif

.if defined(WITH_RUBICON)
DISTFILES+=	marathonRubiconX${EXTRACT_SUFX}:rubicon
EXTRACT_ONLY+=	marathonRubiconX${EXTRACT_SUFX}
PLIST_SUB+=	RUBICON=""
AO_PACKS+=	rubicon
DESKTOP_ENTRIES+="Rubicon X" "" "" "alephone-rubicon" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	RUBICON="@comment "
.endif

.if defined(WITH_TI)
DISTFILES+=	Tempus_Irae${EXTRACT_SUFX}:nardofiles
EXTRACT_ONLY+=	Tempus_Irae${EXTRACT_SUFX}
PLIST_SUB+=	TI=""
AO_PACKS+=	tempus_irae
DESKTOP_ENTRIES+="Tempus Irae" "" "" "alephone-tempus_irae" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	TI="@comment "
.endif

.if defined(WITH_GRAY)
DISTFILES+=	tgi${EXTRACT_SUFX}:gray
EXTRACT_ONLY+=	tgi${EXTRACT_SUFX}
PLIST_SUB+=	GRAY=""
AO_PACKS+=	gray
DESKTOP_ENTRIES+="The Gray Incident" "" "" "alephone-gray" \
		"Game;ActionGame;" false
.else
PLIST_SUB+=	GRAY="@comment "
.endif

.if defined(WITH_PHOENIX)
DISTFILES+=	Phoenix_SE_1.2.0${EXTRACT_SUFX}:phoenix
EXTRACT_ONLY+=	Phoenix_SE_1.2.0${EXTRACT_SUFX}
PLIST_SUB+=	PHOENIX=""
AO_PACKS+=	phoenix
DESKTOP_ENTRIES+="Marathon Phoenix" "" "" "alephone-phoenix" \
	"Game;ActionGame;" false
.else
PLIST_SUB+=	PHOENIX="@comment"
.endif

.if empty(AO_PACKS)
IGNORE=		needs at least one option
.endif

post-extract:
.if defined(WITH_EMR)
	@${TAR} zxf ${DISTDIR}/${DIST_SUBDIR}/${EMR_FILE} -C ${WRKDIR}
	@${MKDIR} ${WRKSRC}/emr
	@cd ${WRKSRC}/${EMR_FILE:S/-0602.tgz//} && \
		${MV} share-emr/* ../emr && \
		${MV} share-doc-emr ../emr/docs && \
		${MV} README ../emr/docs
.endif
.if defined(WITH_ETERNAL)
	@cd ${WRKSRC} && ${MV} "Eternal X 1.0.3" eternal
	@cd ${WRKSRC}/eternal && \
		${FIND} . -type d -print0 | ${XARGS} -0 ${CHMOD} 755 && \
		${FIND} . -type f -print0 | ${XARGS} -0 ${CHMOD} 644
.endif
.if !defined(WITHOUT_EVIL)
	@cd ${WRKSRC} && ${MV} "Marathon EVIL" evil
.endif
.if !defined(WITHOUT_RED)
	@cd ${WRKSRC} && ${MV} "Marathon RED" red
.endif
.if defined(WITH_RUBICON)
	@cd ${WRKSRC} && ${MV} "Rubicon X ƒ" rubicon
.endif
.if defined(WITH_TI)
	@cd ${WRKSRC} && ${MV} Tempus_Irae tempus_irae
	@cd ${WRKSRC}/tempus_irae && \
		${FIND} . -type d -print0 | ${XARGS} -0 ${CHMOD} 755 && \
		${FIND} . -type f -print0 | ${XARGS} -0 ${CHMOD} 644
.endif
.if defined(WITH_GRAY)
	@cd ${WRKSRC} && ${MV} "The Gray Incident" gray
.endif
.if defined(WITH_PHOENIX)
	@cd ${WRKSRC} && ${MV} "Phoenix SE 1.2.0/Marathon Phoenix" phoenix && \
	${MV} "Phoenix SE 1.2.0/Very Specific Changelog.txt" phoenix/ && \
	${MV} "Phoenix SE 1.2.0/The Last Phoenix.txt" phoenix/
.endif

pre-install:
.for f in ${AO_PACKS}
	@cd ${WRKSRC} && ${SED} -e 's|%%GAMEDIR%%|${f}|' wrapper > alephone-${f}
.endfor

do-install:
.for f in ${AO_PACKS}
	${INSTALL_SCRIPT} ${WRKDIR}/alephone-${f} ${PREFIX}/bin
	${CP} -R ${WRKSRC}/${f} ${DATADIR}
	@cd ${DATADIR}/${f} && \
		${FIND} . -type d -print0 | ${XARGS} -0 ${CHMOD} ${BINMODE} && \
		${FIND} . -type f -print0 | ${XARGS} -0 ${CHMOD} ${SHAREMODE}
.endfor
.if defined(WITH_RUBICON)
	@${LN} -s ${DATADIR}/[A-Z]* ${DATADIR}/rubicon
.endif

post-install:
	@${ECHO_CMD}
	@${CAT} ${PKGMESSAGE}
	@${ECHO_CMD}

.include <bsd.port.post.mk>
