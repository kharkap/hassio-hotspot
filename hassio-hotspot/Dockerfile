ARG BUILD_FROM
FROM $BUILD_FROM

LABEL João Loureiro <joaofl@gmail.com> and KharKap

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV LANG C.UTF-8

# Install requirements for add-on
RUN apk update && apk add --no-cache    \
    avahi                               \
    bash jq iw net-tools                \
    sudo busybox-extras                 \
    hostapd iptables                    \
    linux-firmware-other                \
    linux-firmware-brcm                 \
    linux-firmware-ath6k                \
    linux-firmware-ath10k               \
    linux-firmware-ath9k_htc &&         \
    rm -rf /var/cache/apk/* &&          \
	ln -s /lib/firmware/brcm/brcmfmac-ap6330-sdio.txt /lib/firmware/brcm/brcmfmac4330-sdio.rockchip,rk3318-box.txt

COPY hostapd.conf /
COPY udhcpd.conf /etc/udhcpd.conf
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
