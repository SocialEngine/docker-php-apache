#!/bin/bash

function _php_set_xdebug() {
    if [ $# -lt 2 ]; then
        echo "Usage: _php_set_xdebug <ini_dir> <xdebug_status>"

        return 1
    fi

    local ini="${1}/conf.d/docker-php-pecl-xdebug.ini"
    local status=$2

    local status_text="enabled"

    if [[ ${status} == 0 ]]; then
        status_text="disabled"
    fi

    if [[ ${status} == 0 ]] && [[ -f "${ini}" ]]; then
        echo "[PHP] Disabling XDebug";
        mv  ${ini} ${ini}.disabled
    elif [[ ${status} == 1 ]] && [[ -f "${ini}.disabled" ]]; then
        echo "[PHP] Enabling XDebug"
        mv  ${ini}.disabled ${ini}
    else
        echo "[PHP] XDebug is ${status_text}" 
    fi
}
