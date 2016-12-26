#!/bin/bash

function _php_set_timezone() {
    if [ $# -lt 2 ]; then
        echo "Usage: _php_set_timezone <ini_path> <timezone>"

        return 1
    fi

    local timezone="${2}"
    local timezone_file="/usr/share/zoneinfo/${timezone}"
    local ini_path="${1}/conf.d/date_timezone.ini"

    if [ ! -e $timezone_file ]; then
        echo "[PHP] ERROR: \"$timezone_file\" does not exist."

        return 1
    fi

    echo "date.timezone=$timezone" > ${ini_path}
    RETVAL=$?
    if [ $RETVAL -ne 0 ]; then
        return $RETVAL
    fi

    echo "[PHP] Timezone has been set to $timezone"

    return 0
}
