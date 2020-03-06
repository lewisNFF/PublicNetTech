*******************
wireguard
*******************

CentOS 安装wireguard

.. code-block:: console

    yum search wireguard
    sudo curl -Lo /etc/yum.repos.d/wireguard.repo https://copr.fedorainfracloud.org/coprs/jdoss/wireguard/repo/epel-7/jdoss-wireguard-epel-7.repo
    sudo yum install wireguard-dkms wireguard-tools
    ip link add dev wg0 type wireguard
    ip addr add dev wg0 10.1.1.5/24
    wg setconf wg0 /etc/wireguard/wg0.conf
    wg genkey | tee privatekey | wg pubkey > publickey
    vim /etc/wireguard/wg0.conf

    wg-quick up wg0

老外写的很好的文档


