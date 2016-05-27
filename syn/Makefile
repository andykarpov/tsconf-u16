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
       ../rtl/vns2hid/receiver.vhd \
       ../rtl/vns2hid/deserializer.vhd \
       ../rtl/sound/soundrive/soundrive.vhd \
       ../rtl/sound/opll/voicerom.vhd \
       ../rtl/sound/opll/voicememory.vhd \
       ../rtl/sound/opll/vm2413.vhd \
       ../rtl/sound/opll/temporalmixer.vhd \
       ../rtl/sound/opll/slotcounter.vhd \
       ../rtl/sound/opll/sinetable.vhd \
       ../rtl/sound/opll/registermemory.vhd \
       ../rtl/sound/opll/phasememory.vhd \
       ../rtl/sound/opll/phasegenerator.vhd \
       ../rtl/sound/opll/outputmemory.vhd \
       ../rtl/sound/opll/outputgenerator.vhd \
       ../rtl/sound/opll/opll.vhd \
       ../rtl/sound/opll/operator.vhd \
       ../rtl/sound/opll/lineartable.vhd \
       ../rtl/sound/opll/feedbackmemory.vhd \
       ../rtl/sound/opll/envelopememory.vhd \
       ../rtl/sound/opll/envelopegenerator.vhd \
       ../rtl/sound/opll/controller.vhd \
       ../rtl/sound/opll/attacktable.vhd \
       ../rtl/sound/opll/RegisterMemory.vhd \
       ../rtl/sound/opll/PhaseMemory.vhd \
       ../rtl/sound/opll/PhaseGenerator.vhd \
       ../rtl/sound/opll/OutputMemory.vhd \
       ../rtl/sound/opll/OutputGenerator.vhd \
       ../rtl/sound/opll/Opll.vhd \
       ../rtl/sound/opll/Operator.vhd \
       ../rtl/sound/opll/LinearTable.vhd \
       ../rtl/sound/opll/FeedbackMemory.vhd \
       ../rtl/sound/opll/EnvelopeMemory.vhd \
       ../rtl/sound/opll/EnvelopeGenerator.vhd \
       ../rtl/sound/opll/Controller.vhd \
       ../rtl/sound/opll/AttackTable.vhd \
       ../rtl/i2c/i2c.vhd \
       ../rtl/ts/cpu/zsignals.v \
       ../rtl/ts/cpu/zports.v \
       ../rtl/ts/cpu/zmem.v \
       ../rtl/ts/cpu/zmaps.v \
       ../rtl/ts/cpu/zint.v \
       ../rtl/ts/cpu/zclock.v \
       ../rtl/t80/T80s.vhd \
       ../rtl/hdmi/serializer.vhd \
       ../rtl/hdmi/av_hdmi.vhd \
       ../rtl/hdmi/encoder.vhd \
       ../rtl/hdmi/hdmidataencoder.v \
       ../rtl/hdmi/hdmidelay.vhd \
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

QUARTUS_HOME := $(shell dirname `which quartus_pgm`)
PWD := $(shell pwd)
ASSIGNMENT_FILES = $(PROJECT)_$(BOARDFILE).qpf $(PROJECT)_$(BOARDFILE).qsf

###################################################################
# COF file contents
define newline


endef

define COF
<?xml version="1.0" encoding="US-ASCII" standalone="yes"?>
<cof>
	<eprom_name>$(FLASH_CONFIG)</eprom_name>
	<flash_loader_device>$(FLASH_LOADER)</flash_loader_device>
	<output_filename>$(PROJECT)_$(BOARDFILE).jic</output_filename>
	<n_pages>1</n_pages>
	<width>1</width>
	<mode>7</mode>
	<hex_block>
		<hex_filename>../rom/zxevo.hex</hex_filename>
		<hex_addressing>relative</hex_addressing>
		<hex_offset>835584</hex_offset>
	</hex_block>
	<sof_data>
		<start_address>00000000</start_address>
		<user_name>Page_0</user_name>
		<page_flags>1</page_flags>
		<bit0>
			<sof_filename>$(PROJECT)_$(BOARDFILE).sof</sof_filename>
		</bit0>
	</sof_data>
	<version>6</version>
	<create_cvp_file>0</create_cvp_file>
	<auto_create_rpd>0</auto_create_rpd>
	<options>
		<map_file>1</map_file>
	</options>
</cof>
endef
export COF

define CDF
/* Quartus CDF */
JedecChain;
        FileRevision(JESD32A);
        DefaultMfr(6E);

        P ActionCode(Cfg)
                Device PartName($(FLASH_LOADER)) Path("$(PWD)/") File("$(PROJECT)_$(BOARDFILE).jic") MfrSpec(OpMask(1) SEC_Device($(FLASH_CONFIG)) Child_OpMask(1 1));

ChainEnd;

AlteraBegin;
        ChainType(JTAG);
AlteraEnd;
endef
export CDF

###################################################################
# Main Targets
#
# all: build everything
# clean: remove output files and database
# program: program your device with the compiled design
###################################################################

all: smart.log $(PROJECT)_$(BOARDFILE).asm.rpt $(PROJECT)_$(BOARDFILE).sta.rpt $(PROJECT)_$(BOARDFILE).cof

clean: 
	rm -rf *.rpt 
	rm -rf *.chg 
	rm -rf smart.log 
	rm -rf *.htm 
	rm -rf *.eqn 
	rm -rf *.pin 
	rm -rf *.sof 
	rm -rf *.pof 
	rm -rf *.jic 
	rm -rf db 
	rm -rf incremental_db
	rm -rf *.qsf
	rm -rf *.qpf
	rm -rf *.summary
	rm -rf *.smsg
	rm -rf *.cof
	rm -rf *.cdf
	rm -rf *.jdi
	rm -rf *.map
	rm -rf *.sld
	rm -rf PLLJ_PLLSPE_INFO.txt

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
	quartus_sh --prepare -f $(FAMILY) -t $(TOP_LEVEL_ENTITY) $(PROJECT)_$(BOARDFILE) 
	-cat $(BOARDFILE) >> $(PROJECT)_$(BOARDFILE).qsf
	echo "$$COF" > $(PROJECT)_$(BOARDFILE).cof
	echo "$$CDF" > $(PROJECT)_$(BOARDFILE).cdf
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

