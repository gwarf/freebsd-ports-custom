PORTNAME=	marksman
DISTVERSION=	2023-12-09
CATEGORIES=	textproc

MAINTAINER=	baptiste@bapt.name
COMMENT=	 Write Markdown with code assist and intelligence in the comfort of your favourite editor
WWW=	https://github.com/artempyanykh/marksman

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	artempyanykh

BUILD_DEPENDS=	dotnet:lang/dotnet git:devel/git

USES=	gmake
ALL_TARGET= #none
INSTALL_TARGET=	install

# NUGET_GROUPS=	NUGET
# NUPKG_NUGET must be regenerated every time DISTVERSION is changed
# NUPKG_NUGET=	AsyncKeyedLock:6.4.2 \

# MAKE_ENV+=DOTNET_CLI_TELEMETRY_OPTOUT=1

# do-build:
# # 	# @${MKDIR} ${STAGEDIR}${PREFIX}/${PORTNAME}-${DISTVERSION}
# 	#cd ${WRKSRC} && ${GMAKE}
# 	cd ${WRKSRC} \
# 		&& git init \
# 		&& export DOTNET_CLI_TELEMETRY_OPTOUT=1 \
# 		&& ${SETENV} DOTNET_CLI_TELEMETRY_OPTOUT=1 \
# 		&& ${SETENV} DOTNET_CLI_TELEMETRY_OPTOUT=1 dotnet build --configuration Release Marksman.sln
#  	# && dotnet publish --configuration Release Marksman.sln --output "$PWD"/publish

# do-install:
# 	# @${MKDIR} ${STAGEDIR}${PREFIX}/${PORTNAME}-${DISTVERSION}
# 	# cd ${WRKSRC} && ${GMAKE} install
# 	${INSTALL_PROGRAM} ${WRKSRC}/publish ${STAGEDIR}${PREFIX}/bin/muellerfind
# 	${INSTALL_SCRIPT} ${WRKDIR}/mueller ${STAGEDIR}${PREFIX}/bin
# 	@${MKDIR} ${STAGEDIR}${DATADIR}/
# 	${INSTALL_DATA} ${WRKSRC_DIC}/Mueller7accentGPL.ru_RU.* ${STAGEDIR}${DATADIR}/
# 	# cd ${WRKSRC}/publish && ${INSTALL_DATA}
# 	# cd ${WRKSRC}/dist/my${DISTNAME}/ && ${INSTALL_DATA} uk_UA.aff uk_UA.dic ${STAGEDIR}${DATADIR}/

.include <bsd.port.mk>
