# GNU makefile proxy script for BSD make
# Written and maintained by Mahmoud Al-Qudsi <mqudsi@neosmart.net>
# Copyright NeoSmart Technologies <https://neosmart.net/> 2014-2018
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# 1. Redistributions of source code must retain the above copyright notice, this
# list of conditions and the following disclaimer.
#
# 2. Redistributions in binary form must reproduce the above copyright notice,
# this list of conditions and the following disclaimer in the documentation
# and/or other materials provided with the distribution.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

JARG =
GMAKE = "gmake"
#When gmake is called from another make instance, -w is automatically added
#which causes extraneous messages about directory changes to be emitted.
#--no-print-directory silences these messages.
GARGS = "--no-print-directory"

.if "$(.MAKE.JOBS)" != ""
JARG = -j$(.MAKE.JOBS)
.endif

#by default bmake will cd into ./obj first
.OBJDIR: ./

.PHONY: FRC
$(.TARGETS): FRC
	$(GMAKE) $(GARGS) $(.TARGETS:S,.DONE,,) $(JARG)

.DONE .DEFAULT: .SILENT
	$(GMAKE) $(GARGS) $(.TARGETS:S,.DONE,,) $(JARG)

.ERROR: .SILENT
	if ! which $(GMAKE) > /dev/null; then \
		echo "GNU Make is required!"; \
	fi
