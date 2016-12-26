#!/bin/bash

function check_docker_link() {
    if [ $# -lt 3 ]; then
        echo "Usage: check_docker_link <name> <addr> <port>"

        return 1
    fi

    local name=${1}
    local addr=${2}
    local port=${3}

    if test -z "${addr}" -o -z "${port}"; then
        echo "No link for $name found, skipping..."

        return 1
    fi

    local test_url="tcp://$addr:$port"

    while ! exec 6<>/dev/tcp/${addr}/${port}; do
        echo "$(date) - still trying to connect to ${name} at ${test_url}"
        sleep 1
    done

    exec 6>&-
    exec 6<&-
    echo "Connected to ${name} at ${test_url}"

    return 0
}
