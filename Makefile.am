SUBDIRS = .

include @abs_top_builddir@/common.gmake

lib_LIBRARIES = libexchange.a

libexchange_a_SOURCES = @srcdir@/src/AccumulatedVolume.cpp \
												@srcdir@/src/AggregatedTradePriceId.cpp \
												@srcdir@/src/BaseComparableAttributes.cpp \
												@srcdir@/src/BaseComparableContainer.cpp \
												@srcdir@/src/BaseComparable.cpp \
												@srcdir@/src/BaseConsumer.cpp \
												@srcdir@/src/BaseSideContainer.cpp \
												@srcdir@/src/BaseTrade.cpp \
												@srcdir@/src/BookFromSortedLevels.cpp \
												@srcdir@/src/BookFromUnSortedLevels.cpp \
												@srcdir@/src/Channel.cpp \
												@srcdir@/src/CLPModifiedBook.cpp \
												@srcdir@/src/ComparisonResult.cpp \
												@srcdir@/src/EndOfEvent.cpp \
												@srcdir@/src/EndOfFrame.cpp \
												@srcdir@/src/exchange.cpp \
												@srcdir@/src/ExecutionSummary.cpp \
												@srcdir@/src/FastBookFromUnSortedLevels.cpp \
												@srcdir@/src/GapsInfo.cpp \
												@srcdir@/src/Imbalance.cpp \
												@srcdir@/src/Instrument.cpp \
												@srcdir@/src/InstrumentGroup.cpp \
												@srcdir@/src/LevelBookAttributes.cpp \
												@srcdir@/src/LevelBook.cpp \
												@srcdir@/src/LevelBookStats.cpp \
												@srcdir@/src/Level.cpp \
												@srcdir@/src/LPModifiedBook.cpp \
												@srcdir@/src/Lq2Trade.cpp \
												@srcdir@/src/MarketConfig.cpp \
												@srcdir@/src/MarketDataField.cpp \
												@srcdir@/src/MarketDataFieldVector.cpp \
												@srcdir@/src/MarketDataFieldVectorMap.cpp \
												@srcdir@/src/MarketInfo.cpp \
												@srcdir@/src/MessageInfo.cpp \
												@srcdir@/src/ModifiedBook.cpp \
												@srcdir@/src/ModifiedBookFromSortedLevels.cpp \
												@srcdir@/src/ModifiedBookFromSortedLevelsInterface.cpp \
												@srcdir@/src/ModifiedBookImpFromSortedLevels.cpp \
												@srcdir@/src/ModifiedBookInterface.cpp \
												@srcdir@/src/NasdaqImbalance.cpp \
												@srcdir@/src/NXdpImbalance.cpp \
												@srcdir@/src/Order.cpp \
												@srcdir@/src/OrderTable.cpp \
												@srcdir@/src/OrderTableStats.cpp \
												@srcdir@/src/Price.cpp \
												@srcdir@/src/Product.cpp \
												@srcdir@/src/PublishedLevelBook.cpp \
												@srcdir@/src/StaticData.cpp \
												@srcdir@/src/Status.cpp \
												@srcdir@/src/TradeBreakOrCancel.cpp \
												@srcdir@/src/TradeCorrection.cpp \
												@srcdir@/src/Trade.cpp \
												@srcdir@/src/NscmpEnums.cpp

# build unitTest
check_PROGRAMS = unitTest
unitTest_SOURCES = tests/exchangeTest.cpp
unitTest_LDADD = libexchange.a -lcppunit

# build benchTest
bin_PROGRAMS = benchTest
benchTest_SOURCES = benchs/main.cpp
benchTest_LDADD = libexchange.a

# add unitTest in check scripts
check_SCRIPTS = unitTest
TESTS = $(check_SCRIPTS)

##################
# define copy built lib in libs directory
##
cplib: @top_builddir@/lib/libexchange.a

@top_builddir@/lib/libexchange.a: libexchange.a
	-cp libexchange.a @top_builddir@/lib

##################
# define cpplint target
##
cpplint_lib_FILES	 = $(addprefix lint/,  $(notdir $(libexchange_a_SOURCES:%cpp=%stamp)))
cpplint_tests_FILES	 = $(addprefix lint/tests/,  $(notdir $(unitTest_SOURCES:%cpp=%stamp)))

lint_FILES = $(cpplint_lib_FILES) \
								$(cpplint_tests_FILES)

cpplint_FILES=$(shell if test -z $(QUICK_AND_DIRTY) ; then echo $(lint_FILES); else echo ""; fi)

cpplint: $(cpplint_FILES)

lint/%.stamp: @srcdir@/src/%.cpp
	@-mkdir -p lint
	@$(CPPLINT) $(CPPLINTOPTS) $^ 2>&1
	@echo Timestamp > $@ 

lint/tests/%.stamp: @srcdir@/tests/%.cpp
	@-mkdir -p lint/tests
	@$(CPPLINT) $(CPPLINTOPTS) $^ 2>&1
	@echo Timestamp > $@ 

all-local: cplib cpplint

CLEANFILES = $(check_PROGRAMS) \
						 $(cpplint_FILES) \
						 @top_builddir@/lib/libexchange.a

.PHONY: cplib cpplint
