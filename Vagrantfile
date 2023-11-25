Vagrant.configure("2") do |config|

    config.vm.define :router do |router|
        router.vm.box = "debian/bookworm64"
        router.vm.hostname="router"
        router.vm.synced_folder ".", "/vagrant", disabled: true
        router.vm.network :public_network,
            :dev => "br0",
            :mode => "bridge",
            :type => "bridge",
            :use_dhcp_assigned_default_route => true
        router
        router.vm.network :private_network,
            :libvirt__network_name => "red_intra",
            :libvirt__dhcp_enabled => false,
            :ip => "10.0.0.1",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
    end

    config.vm.define :web do |web|
        web.vm.box = "debian/bookworm64"
        web.vm.hostname="web"
        web.vm.synced_folder ".", "/vagrant", disabled: true
        web.vm.network :private_network,
            :libvirt__network_name => "red_intra",
            :libvirt__dhcp_enabled => false,
            :ip => "10.0.0.2",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
        web.vm.network :private_network,
            :libvirt__network_name => "red_datos",
            :libvirt__dhcp_enabled => false,
            :ip => "10.1.0.2",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
    end
    
    config.vm.define :bd do |bd|
        bd.vm.box = "debian/bookworm64"
        bd.vm.hostname="bd"
        bd.vm.synced_folder ".", "/vagrant", disabled: true
        bd.vm.network :private_network,
            :libvirt__network_name => "red_intra",
            :libvirt__dhcp_enabled => false,
            :ip => "10.0.0.3",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
        bd.vm.network :private_network,
            :libvirt__network_name => "red_datos",
            :libvirt__dhcp_enabled => false,
            :ip => "10.1.0.3",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
    end

    config.vm.define :cliente do |cliente|
        cliente.vm.box = "debian/bookworm64"
        cliente.vm.hostname="cliente"
        cliente.vm.synced_folder ".", "/vagrant", disabled: true
        cliente.vm.network :private_network,
            :libvirt__network_name => "red_intra",
            :libvirt__dhcp_enabled => false,
            :ip => "10.0.0.4",
            :netmask => "16",
            :libvirt__forward_mode => "veryisolated"
    end
end
