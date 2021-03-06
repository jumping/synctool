#! /usr/bin/make
#
#	synctool Makefile	WJ109
#

PREFIX=/opt/synctool
SBINDIR=$(PREFIX)/sbin

INSTALL=/usr/bin/install
MKDIR=/bin/mkdir

MASTERDIR=/var/lib/synctool
MASTERBIN=$(MASTERDIR)/sbin

SCRIPTS=synctool.py synctool_config.py  synctool_master.py synctool_aggr.py \
	synctool_ping.py synctool_ssh.py synctool_scp.py synctool_master_pkg.py \
	synctool_pkg.py

LIBS=synctool_lib.py synctool_stat.py synctool_object.py \
	synctool_update.py synctool_unbuffered.py \
	synctool_overlay.py synctool_nodeset.py synctool_param.py \
	synctool_configparser.py synctool_pkgclass.py \
	synctool_pkg_aptget.py synctool_pkg_yum.py synctool_pkg_zypper.py \
	synctool_pkg_pacman.py synctool_pkg_brew.py synctool_pkg_bsdpkg.py

all:
	@echo "synctool Makefile"
	@echo
	@echo "First edit the Makefile and adjust the PREFIX"
	@echo "Install PREFIX is currently set to:" $(PREFIX)
	@echo
	@echo "type 'make install' to install synctool on the server"
	@echo

install:
	@echo masterdir is $(MASTERDIR)
	@mkdir -m 700 -p $(MASTERDIR)
	@mkdir -m 755 -p $(MASTERDIR)/overlay $(MASTERDIR)/delete $(MASTERDIR)/scripts $(MASTERDIR)/tasks
	@echo installing synctool server commands to $(MASTERBIN)
	@mkdir -m 755 -p $(MASTERBIN)
	@install -m 755 $(SCRIPTS) $(MASTERBIN)
	@install -m 644 $(LIBS) $(MASTERBIN)
	@rm -f $(MASTERBIN)/synctool_core.py
	@echo linking synctool server commands to $(SBINDIR)/
	@mkdir -m 755 -p $(SBINDIR)
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_master.py synctool )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_master.py synctool-master )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_config.py synctool-config )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_ping.py synctool-ping )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_ping.py dsh-ping )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_ssh.py synctool-ssh )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_ssh.py dsh )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_scp.py synctool-scp )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_scp.py dcp )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_aggr.py synctool-aggr )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_aggr.py aggr )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_master_pkg.py synctool-pkg )
	@( cd $(SBINDIR) && ln -sf $(MASTERBIN)/synctool_master_pkg.py dsh-pkg )

# EOB
