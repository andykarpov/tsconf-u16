###################################################################
# ReVerSE U16 Project Makefile v1.0
# 
# Specify the basename of the design (project) and top level entity
###################################################################

PROJECT = u16_tsconf
TOP_LEVEL_ENTITY = tsconf

###################################################################
# Part, Family, Boardfile revA or revC, Flash loader device, etc

FAMILY = "Cyclone IV E"
PART = EP4CE22E22C8
FLASH_CONFIG = EPCS16
FLASH_LOADER = EP4CE22
BOARDFILE = revA

###################################################################
# Sources

SRCS = ../rtl/t80/T80se.vhd \
       ../rtl/t80/T80_Reg.vhd \
       ../rtl/t80/T80_Pack.vhd \
       ../rtl/t80/T80_MCode.vhd \
       ../rtl/t80/T80_ALU.vhd \
       ../rtl/t80/T80.vhd \
       ../rtl/hid/receiver.vhd \
       ../rtl/hid/deserializer.vhd \
       ../rtl/sound/soundrive/soundrive.vhd \
       ../rtl/i2c/i2c.vhd \
       ../rtl/ts/cpu/zsignals.v \
       ../rtl/ts/cpu/zports.v \
       ../rtl/ts/cpu/zmem.v \
       ../rtl/ts/cpu/zmaps.v \
       ../rtl/ts/cpu/zint.v \
       ../rtl/ts/cpu/zclock.v \
       ../rtl/t80/T80s.vhd \
       ../rtl/hdmi/altddio_out1.vhd \
       ../rtl/hdmi/hdmi.vhd \
       ../rtl/hdmi/encoder.vhd \
       ../rtl/hdmi/hdmidataencoder.v \
       ../rtl/dac/dac.vhd \
       ../rtl/tsconf.vhd \
       ../rtl/pll/altpll0.vhd \
       ../rtl/rtc/mc146818a.vhd \
       ../rtl/rtc/CMOS.vhd \
       ../rtl/sdram/sdram.vhd \
       ../rtl/spi/spi_flash.vhd \
       ../rtl/ts/memory/dma.v \
       ../rtl/ts/memory/arbiter.v \
       ../rtl/ts/common/spi.v \
       ../rtl/ts/pll/pll.v \
       ../rtl/ts/pll/clock_2.v \
       ../rtl/ts/pll/clock_1.vhd \
       ../rtl/ts/pll/clock.v \
       ../rtl/ts/sound/sound.v \
       ../rtl/ts/video/video_ts_render.v \
       ../rtl/ts/video/video_ts.v \
       ../rtl/ts/video/video_top.v \
       ../rtl/ts/video/video_sync.v \
       ../rtl/ts/video/video_render.v \
       ../rtl/ts/video/video_ports.v \
       ../rtl/ts/video/video_out.v \
       ../rtl/ts/video/video_mode.v \
       ../rtl/ts/video/video_fetch.v \
       ../rtl/ts/video/mem/video_vmem.v \
       ../rtl/ts/video/mem/video_tsline1.v \
       ../rtl/ts/video/mem/video_tsline0.v \
       ../rtl/ts/video/mem/video_tmbuf.v \
       ../rtl/ts/video/mem/video_sfile.v \
       ../rtl/ts/video/mem/video_cram.v \
       ../rtl/ts/cpu/memory/cache_data.v \
       ../rtl/ts/cpu/memory/cache_addr.v \
       ../rtl/rom/rom.vhd \
       ../rtl/ts/video/lut.vhd \
       ../rtl/sound/turbosound/vol_table_array.vhd \
       ../rtl/sound/turbosound/turbosound.vhd \
       ../rtl/sound/turbosound/ym2149.vhd \

###################################################################
# Additional variables

PWD := $(shell pwd)
QUARTUS_HOME := $(shell dirname `which quartus_pgm`)
ASSIGNMENT_FILES = $(PROJECT)_$(BOARDFILE).qpf $(PROJECT)_$(BOARDFILE).qsf

###################################################################
# Main Targets
#
# all: build everything
# clean: remove output files and database
# program: program your device with the compiled design
###################################################################

all: smart.log $(PROJECT)_$(BOARDFILE).asm.rpt $(PROJECT)_$(BOARDFILE).sta.rpt $(PROJECT)_$(BOARDFILE).cof

clean: 
	rm -f *.rpt \
		*.chg \
		smart.log \
		*.htm \
		*.eqn \
		*.pin \
		*.sof \
		*.pof \
		*.jic \
		*.qsf \
		*.qpf \
		*.summary \
		*.smsg \
		*.cof \
		*.cdf \
		*.jdi \
		*.map \
		*.sld \
		PLLJ_PLLSPE_INFO.txt \
		../loader/loader.bin \
		../loader/loader.hex \
		../loader/info.asm \
		../rom/*.hex \

	rm -rf db \
		incremental_db \

map: smart.log $(PROJECT)_$(BOARDFILE).map.rpt
fit: smart.log $(PROJECT)_$(BOARDFILE).fit.rpt
asm: smart.log $(PROJECT)_$(BOARDFILE).asm.rpt
sta: smart.log $(PROJECT)_$(BOARDFILE).sta.rpt
smart: smart.log

###################################################################
# Executable Configuration
###################################################################

MAP_ARGS = --read_settings_files=on $(addprefix --source=,$(SRCS))

FIT_ARGS = --part=$(PART) --read_settings_files=on
ASM_ARGS =
STA_ARGS =

###################################################################
# Target implementations
###################################################################

STAMP = echo done >

$(PROJECT)_$(BOARDFILE).map.rpt: map.chg $(SOURCE_FILES) 
	quartus_map $(MAP_ARGS) $(PROJECT)_$(BOARDFILE)
	$(STAMP) fit.chg

$(PROJECT)_$(BOARDFILE).fit.rpt: fit.chg $(PROJECT)_$(BOARDFILE).map.rpt
	quartus_fit $(FIT_ARGS) $(PROJECT)_$(BOARDFILE)
	$(STAMP) asm.chg
	$(STAMP) sta.chg

$(PROJECT)_$(BOARDFILE).asm.rpt: asm.chg $(PROJECT)_$(BOARDFILE).fit.rpt
	quartus_asm $(ASM_ARGS) $(PROJECT)_$(BOARDFILE)

$(PROJECT)_$(BOARDFILE).sta.rpt: sta.chg $(PROJECT)_$(BOARDFILE).fit.rpt
	quartus_sta $(STA_ARGS) $(PROJECT)_$(BOARDFILE) 

smart.log: $(ASSIGNMENT_FILES)
	quartus_sh --determine_smart_action $(PROJECT)_$(BOARDFILE) > smart.log

###################################################################
# Project initialization
###################################################################

$(ASSIGNMENT_FILES):

	./build $(PROJECT) $(BOARDFILE) $(PART) $(FLASH_LOADER) $(FLASH_CONFIG)
	quartus_sh --prepare -f $(FAMILY) -t $(TOP_LEVEL_ENTITY) $(PROJECT)_$(BOARDFILE) 
	-cat $(BOARDFILE) >> $(PROJECT)_$(BOARDFILE).qsf
map.chg:
	$(STAMP) map.chg
fit.chg:
	$(STAMP) fit.chg
sta.chg:
	$(STAMP) sta.chg
asm.chg:
	$(STAMP) asm.chg

###################################################################
# Generate jic file
###################################################################

jic: $(PROJECT)_$(BOARDFILE).cof 
	quartus_cpf -c "$(PROJECT)_$(BOARDFILE).cof"

###################################################################
# Programming the device
###################################################################

programsof: $(PROJECT)_$(BOARDFILE).sof
	quartus_pgm --no_banner --mode=jtag -o "P;$(PROJECT)_$(BOARDFILE).sof"

program: $(PROJECT)_$(BOARDFILE).cdf
	quartus_pgm --no_banner "$(PROJECT)_$(BOARDFILE).cdf"

