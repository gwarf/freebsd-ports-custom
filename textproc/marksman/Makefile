PORTNAME=	marksman
DISTVERSION=	2023-12-09
CATEGORIES=	textproc
# Will get the files via git
DISTFILES=

MAINTAINER=	baptiste@bapt.name
COMMENT=	 Write Markdown with code assist and intelligence in the comfort of your favourite editor
WWW=	https://github.com/artempyanykh/marksman

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

# XXX: can be used to fetch an export of a given tag
# USE_GITHUB=	yes
# USE_GITHUB=	nodefault
# GH_TAGNAME=	${DISTVERSION}
GH_ACCOUNT=	artempyanykh
GIT_URL=	https://github.com/${GH_ACCOUNT}/${PORTNAME}

FETCH_DEPENDS=	git:devel/git
BUILD_DEPENDS=	dotnet:lang/dotnet git:devel/git

# NUGET_GROUPS=	NUGET
# NUPKG_NUGET must be regenerated every time DISTVERSION is changed
# NUPKG_NUGET=	AsyncKeyedLock:6.4.2 \

# The build process needs to access the git repository
# Thus we clone it and archive it with the .git folder
do-fetch:
	${MKDIR} ${DISTDIR}/${DIST_SUBDIR} && \
	cd ${DISTDIR}/${DIST_SUBDIR} && \
	git clone -q -b ${DISTVERSION} ${GIT_URL} ${PORTNAME}-${DISTVERSION} && \
	cd ${PORTNAME}-${DISTVERSION} && \
	${FIND} . -print0 | \
	${TAR} czf ${DISTDIR}/${DIST_SUBDIR}/${PORTNAME}-${DISTVERSION}${EXTRACT_SUFX} --null -T - && \
	cd ${DISTDIR}/${DIST_SUBDIR} && \
	${RM} -r ${PORTNAME}-${DISTVERSIONFULL}

do-extract:
	${MKDIR} ${WRKSRC} && \
		${TAR} xzf ${DISTDIR}/${PORTNAME}-${DISTVERSION}${EXTRACT_SUFX} -C ${WRKSRC}

do-build:
	cd ${WRKSRC} && \
	export DOTNET_CLI_TELEMETRY_OPTOUT=1 && \
	${SETENV} DOTNET_CLI_TELEMETRY_OPTOUT=1 dotnet build --configuration Release Marksman.sln && \
	${SETENV} DOTNET_CLI_TELEMETRY_OPTOUT=1 dotnet publish --configuration Release Marksman.sln \
		--output ${WRKSRC}/publish

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}/
	#XXX: use COPYTREE_SHARE cf jellyfin?
	cp -r ${WRKSRC}/publish/ ${STAGEDIR}${DATADIR}/marksman
	#XXX: add a wrapper script instead?
	${INSTALL_PROGRAM} ${WRKSRC}/publish/marksman ${STAGEDIR}${PREFIX}/bin/marksman

.include <bsd.port.mk>
