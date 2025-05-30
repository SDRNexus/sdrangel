project(samplesource)

add_subdirectory(fileinput)
add_subdirectory(testsource)
add_subdirectory(localinput)

if (CM256CC_FOUND AND (HAS_SSE3 OR HAS_NEON))
    add_subdirectory(remoteinput)
else()
    message(STATUS "Not building remoteinput (CM256CC_FOUND=${CM256CC_FOUND} HAS_SSE3=${HAS_SSE3} HAS_NEON=${HAS_NEON})")
endif()

if(ENABLE_AIRSPY AND LIBAIRSPY_FOUND)
    add_subdirectory(airspy)
else()
    message(STATUS "Not building airspy (ENABLE_AIRSPY=${ENABLE_AIRSPY} LIBAIRSPY_FOUND=${LIBAIRSPY_FOUND})")
endif()

if(ENABLE_AIRSPYHF AND LIBAIRSPYHF_FOUND)
    add_subdirectory(airspyhf)
else()
    message(STATUS "Not building airspyhf (ENABLE_AIRSPYHF=${ENABLE_AIRSPYHF} LIBAIRSPYHF_FOUND=${LIBAIRSPYHF_FOUND})")
endif()

if(ENABLE_BLADERF AND LIBBLADERF_FOUND)
    add_subdirectory(bladerf1input)
    add_subdirectory(bladerf2input)
else()
    message(STATUS "Not building bladerf1input or bladerf2input (ENABLE_BLADERF=${ENABLE_BLADERF} LIBBLADERF_FOUND=${LIBBLADERF_FOUND})")
endif()

if(ENABLE_FUNCUBE AND LIBUSB_FOUND AND HIDAPI_FOUND)
    add_subdirectory(fcdpro)
    add_subdirectory(fcdproplus)
else()
    message(STATUS "Not building fcdpro or fcdproplus (ENABLE_FUNCUBE=${ENABLE_FUNCUBE} LIBUSB_FOUND=${LIBUSB_FOUND} HIDAPI_FOUND=${HIDAPI_FOUND})")
endif()

if(ENABLE_HACKRF AND LIBHACKRF_FOUND)
    add_subdirectory(hackrfinput)
else()
    message(STATUS "Not building hackrfinput (ENABLE_HACKRF=${ENABLE_HACKRF} LIBHACKRF_FOUND=${LIBHACKRF_FOUND})")
endif()

if(ENABLE_LIMESUITE AND LIMESUITE_FOUND)
    add_subdirectory(limesdrinput)
else()
    message(STATUS "Not building limesdrinput (ENABLE_LIMESUITE=${ENABLE_LIMESUITE} LIMESUITE_FOUND=${LIMESUITE_FOUND})")
endif()

if(ENABLE_MIRISDR AND LIBMIRISDR_FOUND)
    add_subdirectory(sdrplay)
else()
    message(STATUS "Not building sdrplay (ENABLE_MIRISDR=${ENABLE_MIRISDR} LIBMIRISDR_FOUND=${LIBMIRISDR_FOUND})")
endif()

if(ENABLE_SDRPLAY AND SDRPLAY_FOUND)
    add_subdirectory(sdrplayv3)
else()
    message(STATUS "Not building sdrplayv3 (ENABLE_SDRPLAY=${ENABLE_SDRPLAY} SDRPLAY_FOUND=${SDRPLAY_FOUND})")
endif()

if(ENABLE_PERSEUS AND LIBPERSEUS_FOUND AND RX_SAMPLE_24BIT)
    add_subdirectory(perseus)
else()
    message(STATUS "Not building perseus (ENABLE_PERSEUS=${ENABLE_PERSEUS} LIBPERSEUS_FOUND=${LIBPERSEUS_FOUND} RX_SAMPLE_24BIT=${RX_SAMPLE_24BIT})")
endif()

if(ENABLE_XTRX AND LIBXTRX_FOUND)
    add_subdirectory(xtrxinput)
else()
    message(STATUS "Not building xtrxinput (ENABLE_XTRX=${ENABLE_XTRX} LIBXTRX_FOUND=${LIBXTRX_FOUND})")
endif()

if(ENABLE_IIO AND LIBIIO_FOUND)
    add_subdirectory(plutosdrinput)
else()
    message(STATUS "Not building plutosdrinput (ENABLE_IIO=${ENABLE_IIO} LIBIIO_FOUND=${LIBIIO_FOUND})")
endif()

if(ENABLE_RTLSDR AND LIBRTLSDR_FOUND)
    add_subdirectory(rtlsdr)
else()
    message(STATUS "Not building rtlsdr (ENABLE_RTLSDR=${ENABLE_RTLSDR} LIBRTLSDR_FOUND=${LIBRTLSDR_FOUND})")
endif()

if(ENABLE_SOAPYSDR AND SOAPYSDR_FOUND)
    add_subdirectory(soapysdrinput)
else()
    message(STATUS "Not building soapysdrinput (ENABLE_SOAPYSDR=${ENABLE_SOAPYSDR} SOAPYSDR_FOUND=${SOAPYSDR_FOUND})")
endif()

if(LIBSIGMF_FOUND)
    add_subdirectory(sigmffileinput)
else()
    message(STATUS "Not building sigmffileinput (LIBSIGMF_FOUND=${LIBSIGMF_FOUND})")
endif()

if(ENABLE_USRP AND UHD_FOUND)
    add_subdirectory(usrpinput)
else()
    message(STATUS "Not building usrpinput (ENABLE_USRP=${ENABLE_USRP} UHD_FOUND=${UHD_FOUND})")
endif()

add_subdirectory(audioinput)
add_subdirectory(kiwisdr)
add_subdirectory(remotetcpinput)

if(ENABLE_AARONIARTSA AND NOT ANDROID)
    add_subdirectory(aaroniartsainput)
else()
    message(STATUS "Not building aaroniartsainput (ENABLE_AARONIARTSA=${ENABLE_AARONIARTSA})")
endif()

if(ANDROID)
    add_subdirectory(androidsdrdriverinput)
endif()
