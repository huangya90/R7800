#
# Copyright (C) 2006-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=iptables
PKG_VERSION:=1.8.5
PKG_RELEASE:=1

PKG_MD5SUM:=42cfa96d4ac5eb93ee7ed8dd85cfe8fb
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.netfilter.org/projects/iptables/files \
	ftp://ftp.be.netfilter.org/pub/netfilter/iptables/ \
	ftp://ftp.de.netfilter.org/pub/netfilter/iptables/ \
	ftp://ftp.no.netfilter.org/pub/netfilter/iptables/

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
ifeq ($(DUMP),)
  -include $(LINUX_DIR)/.config
  include $(INCLUDE_DIR)/netfilter.mk
  STAMP_CONFIGURED:=$(strip $(STAMP_CONFIGURED))_$(shell $(SH_FUNC) grep 'NETFILTER' $(LINUX_DIR)/.config | md5s)
endif


define Package/iptables/Default
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Firewall
  URL:=http://netfilter.org/
endef

define Package/iptables/Module
$(call Package/iptables/Default)
  DEPENDS:=iptables $(1)
endef

define Package/iptables
$(call Package/iptables/Default)
  TITLE:=IPv4 firewall administration tool
  MENU:=1
  DEPENDS+= +kmod-ipt-core +libip4tc +libxtables
endef

define Package/iptables/description
IPv4 firewall administration tool.

 Matches:
  - icmp
  - tcp
  - udp
  - comment
  - limit
  - mac
  - multiport

 Targets:
  - ACCEPT
  - DROP
  - REJECT
  - LOG
  - TCPMSS

 Tables:
  - filter
  - mangle

endef

define Package/iptables-mod-conntrack-extra
$(call Package/iptables/Module, +kmod-ipt-conntrack-extra)
  TITLE:=Extra connection tracking extensions
endef

define Package/iptables-mod-conntrack-extra/description
Extra iptables extensions for connection tracking.

 Matches:
  - connbytes
  - connmark
  - recent
  - helper

 Targets:
  - CONNMARK

endef

define Package/iptables-mod-conntrack-qos
$(call Package/iptables/Module, +kmod-ipt-conntrack-qos)
  TITLE:=QoS connection tracking extensions
endef

define Package/iptables-mod-conntrack-qos/description
QoS iptables extensions for connection tracking.

 Targets:
  - DSCPREMARK
  - VLANTAG

endef

define Package/iptables-mod-filter
$(call Package/iptables/Module, +kmod-ipt-filter)
  TITLE:=Content inspection extensions
endef

define Package/iptables-mod-filter/description
iptables extensions for packet content inspection.
Includes support for:

 Matches:
  - layer7
  - string

endef

define Package/iptables-mod-ipopt
$(call Package/iptables/Module, +kmod-ipt-ipopt)
  TITLE:=IP/Packet option extensions
endef

define Package/iptables-mod-ipopt/description
iptables extensions for matching/changing IP packet options.

 Matches:
  - dscp
  - ecn
  - length
  - mark
  - statistic
  - tcpmss
  - time
  - unclean
  - hl

 Targets:
  - DSCP
  - CLASSIFY
  - ECN
  - MARK
  - HL

endef

define Package/iptables-mod-ipsec
$(call Package/iptables/Module, +kmod-ipt-ipsec)
  TITLE:=IPsec extensions
endef

define Package/iptables-mod-ipsec/description
iptables extensions for matching ipsec traffic.

 Matches:
  - ah
  - esp
  - policy

endef

define Package/iptables-mod-ipset
$(call Package/iptables/Module,)
  TITLE:=IPset iptables extensions
endef

define Package/iptables-mod-ipset/description
IPset iptables extensions.

 Matches:
  - set

 Targets:
  - SET

endef

define Package/iptables-mod-nat-extra
$(call Package/iptables/Module, +kmod-ipt-nat-extra)
  TITLE:=Extra NAT extensions
endef

define Package/iptables-mod-nat-extra/description
iptables extensions for extra NAT targets.

 Targets:
  - MIRROR
  - NETMAP
  - REDIRECT
endef

define Package/iptables-mod-ulog
$(call Package/iptables/Module, +kmod-ipt-ulog)
  TITLE:=user-space packet logging
endef

define Package/iptables-mod-ulog/description
iptables extensions for user-space packet logging.

 Targets:
  - ULOG

endef

define Package/iptables-mod-hashlimit
$(call Package/iptables/Module, +kmod-ipt-hashlimit)
  TITLE:=hashlimit matching
endef

define Package/iptables-mod-hashlimit/description
iptables extensions for hashlimit matching

 Matches:
  - hashlimit

endef

define Package/iptables-mod-iprange
$(call Package/iptables/Module, +kmod-ipt-iprange)
  TITLE:=IP range extension
endef

define Package/iptables-mod-iprange/description
iptables extensions for matching ip ranges.

 Matches:
  - iprange

endef

define Package/iptables-mod-extra
$(call Package/iptables/Module, +kmod-ipt-extra)
  TITLE:=Other extra iptables extensions
endef

define Package/iptables-mod-extra/description
Other extra iptables extensions.

 Matches:
  - condition
  - owner
  - physdev (if ebtables is enabled)
  - pkttype
  - quota

endef

define Package/iptables-mod-led
$(call Package/iptables/Module, +kmod-ipt-led)
  TITLE:=LED trigger iptables extension
endef

define Package/iptables-mod-led/description
iptables extension for triggering a LED.

 Targets:
  - LED

endef

define Package/iptables-mod-tproxy
$(call Package/iptables/Module, +kmod-ipt-tproxy)
  TITLE:=Transparent proxy iptables extensions
endef

define Package/iptables-mod-tproxy/description
Transparent proxy iptables extensions.

 Matches:
  - socket

 Targets:
  - TPROXY

endef

define Package/iptables-mod-tee
$(call Package/iptables/Module, +kmod-ipt-tee)
  TITLE:=TEE iptables extensions
endef

define Package/iptables-mod-tee/description
TEE iptables extensions.

 Targets:
  - TEE

endef

define Package/iptables-mod-u32
$(call Package/iptables/Module, +kmod-ipt-u32)
  TITLE:=U32 iptables extensions
endef

define Package/iptables-mod-u32/description
U32 iptables extensions.

 Matches:
  - u32

endef

define Package/iptables-mod-mark2prio
$(call Package/iptables/Module, +kmod-ipt-mark2prio)
  TITLE:=mark2prio extension
endef

define Package/iptables-mod-ct-sctp
$(call Package/iptables/Module, +kmod-ipt-ct-sctp)
  TITLE:=SCTP conntrack extension
endef

define Package/iptables-mod-sctp
$(call Package/iptables/Module, +kmod-ipt-sctp)
  TITLE:=SCTP iptables extension
endef

define Package/ip6tables
$(call Package/iptables/Default)
  DEPENDS:=+kmod-ip6tables +libip6tc +libxtables
  CATEGORY:=IPv6
  TITLE:=IPv6 firewall administration tool
  MENU:=1
endef

define Package/libip4tc
$(call Package/iptables/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=IPv4 firewall - shared libiptc library
  ABI_VERSION:=2
  DEPENDS:=+libxtables
endef

define Package/libip6tc
$(call Package/iptables/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=IPv6 firewall - shared libiptc library
  ABI_VERSION:=2
  DEPENDS:=+libxtables
endef

define Package/libxtables
 $(call Package/iptables/Default)
 SECTION:=libs
 CATEGORY:=Libraries
 TITLE:=IPv4/IPv6 firewall - shared xtables library
 DEPENDS:= \
	+IPTABLES_CONNLABEL:libnetfilter-conntrack \
	+IPTABLES_NFTABLES:libnftnl
endef

define Package/libipq
  $(call Package/iptables/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=IPv4/IPv6 firewall - shared libipq library
endef

TARGET_CPPFLAGS := \
	-I$(PKG_BUILD_DIR)/include \
	-I$(LINUX_DIR)/user_headers/include \
	$(TARGET_CPPFLAGS)

TARGET_CFLAGS += \
	-I$(PKG_BUILD_DIR)/include \
	-I$(LINUX_DIR)/user_headers/include \
	-ffunction-sections -fdata-sections \
	-DNO_LEGACY

TARGET_LDFLAGS += \
	-Wl,--gc-sections

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \
	--enable-devel \
	--with-kernel="$(LINUX_DIR)/user_headers" \
	--with-xtlibdir=/usr/lib/iptables \
	--with-xt-lock-name=/var/run/xtables.lock \
	$(if $(CONFIG_IPTABLES_CONNLABEL),,--disable-connlabel) \
	$(if $(CONFIG_IPTABLES_NFTABLES),,--disable-nftables) \
	$(if $(CONFIG_IPV6),,--disable-ipv6)

MAKE_FLAGS := \
	$(TARGET_CONFIGURE_OPTS) \
	COPT_FLAGS="$(TARGET_CFLAGS)" \
	KERNEL_DIR="$(LINUX_DIR)/user_headers/" PREFIX=/usr \
	KBUILD_OUTPUT="$(LINUX_DIR)" \
	BUILTIN_MODULES="$(patsubst ipt_%,%,$(patsubst xt_%,%,$(IPT_BUILTIN) $(IPT_CONNTRACK-m) $(IPT_CONNTRACK_QOS-m) $(IPT_NAT-m)))"

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/include/iptables
	$(INSTALL_DIR) $(1)/usr/include/net/netfilter

	# XXX: iptables header fixup, some headers are not installed by iptables anymore
	$(CP) $(PKG_BUILD_DIR)/include/iptables/*.h $(1)/usr/include/iptables/
	$(CP) $(PKG_BUILD_DIR)/include/iptables.h $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/include/ip6tables.h $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/include/libipulog $(1)/usr/include/
	$(CP) $(PKG_BUILD_DIR)/include/libiptc $(1)/usr/include/

	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libxtables.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libip*tc.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/xtables.pc $(1)/usr/lib/pkgconfig/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libip*tc.pc $(1)/usr/lib/pkgconfig/

	# XXX: needed by firewall3
	$(CP) $(PKG_BUILD_DIR)/extensions/libiptext*.so $(1)/usr/lib/
endef

define Package/iptables/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/xtables-legacy-multi $(1)/usr/sbin/
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/iptables{,-restore,-save} $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/lib/iptables
endef

define Package/ip6tables/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/sbin/ip6tables{,-restore,-save} $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/lib/iptables
	(cd $(PKG_INSTALL_DIR)/usr/lib/iptables ; \
		$(CP) libip6t_*.so $(1)/usr/lib/iptables/ \
	)
endef

define Package/libip4tc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libip4tc.so.* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/extensions/libiptext4.so $(1)/usr/lib/
endef

define Package/libip6tc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libip6tc.so.* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/extensions/libiptext6.so $(1)/usr/lib/
endef

define Package/libxtables/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libxtables.so.* $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/extensions/libiptext.so $(1)/usr/lib/
endef

define Package/libipq/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libipq.so* $(1)/usr/lib/
endef

define BuildPlugin
  define Package/$(1)/install
	$(INSTALL_DIR) $$(1)/usr/lib/iptables
	for m in $(patsubst xt_%,ipt_%,$(2)) $(patsubst ipt_%,xt_%,$(2)); do \
		if [ -f $(PKG_INSTALL_DIR)/usr/lib/iptables/lib$$$$$$$${m}.so ]; then \
			$(CP) $(PKG_INSTALL_DIR)/usr/lib/iptables/lib$$$$$$$${m}.so $$(1)/usr/lib/iptables/ ; \
		fi; \
	done
	$(3)
  endef

  $$(eval $$(call BuildPackage,$(1)))
endef

L7_INSTALL:=\
	$(INSTALL_DIR) $$(1)/etc/l7-protocols; \
	$(CP) files/l7/*.pat $$(1)/etc/l7-protocols/


$(eval $(call BuildPackage,iptables))
$(eval $(call BuildPlugin,iptables-mod-conntrack-extra,$(IPT_CONNTRACK_EXTRA-m)))
$(eval $(call BuildPlugin,iptables-mod-conntrack-qos,$(IPT_CONNTRACK_QOS-m)))
$(eval $(call BuildPlugin,iptables-mod-extra,$(IPT_EXTRA-m)))
$(eval $(call BuildPlugin,iptables-mod-filter,$(IPT_FILTER-m),$(L7_INSTALL)))
$(eval $(call BuildPlugin,iptables-mod-ipopt,$(IPT_IPOPT-m)))
$(eval $(call BuildPlugin,iptables-mod-ipsec,$(IPT_IPSEC-m)))
$(eval $(call BuildPlugin,iptables-mod-ipset,ipt_set ipt_SET))
$(eval $(call BuildPlugin,iptables-mod-nat-extra,$(IPT_NAT_EXTRA-m)))
$(eval $(call BuildPlugin,iptables-mod-iprange,$(IPT_IPRANGE-m)))
$(eval $(call BuildPlugin,iptables-mod-ulog,$(IPT_ULOG-m)))
$(eval $(call BuildPlugin,iptables-mod-hashlimit,$(IPT_HASHLIMIT-m)))
$(eval $(call BuildPlugin,iptables-mod-led,$(IPT_LED-m)))
$(eval $(call BuildPlugin,iptables-mod-tproxy,$(IPT_TPROXY-m)))
$(eval $(call BuildPlugin,iptables-mod-tee,$(IPT_TEE-m)))
$(eval $(call BuildPlugin,iptables-mod-u32,$(IPT_U32-m)))
$(eval $(call BuildPlugin,iptables-mod-mark2prio,$(IPT_MARK2PRIO-m)))
$(eval $(call BuildPlugin,iptables-mod-ct-sctp,$(IPT_CT_SCTP-m)))
$(eval $(call BuildPlugin,iptables-mod-sctp,$(IPT_SCTP-m)))
$(eval $(call BuildPackage,ip6tables))
$(eval $(call BuildPackage,libip4tc))
$(eval $(call BuildPackage,libip6tc))
$(eval $(call BuildPackage,libxtables))
$(eval $(call BuildPackage,libipq))
