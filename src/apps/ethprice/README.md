## ethprice

The `ethprice` tool provides Ethereum price data to various `quickBlocks` tools or for other purposes. Currently, the tool retrieves data in five minute increments through the Poloniex API. In the future, we will add other sources of pricing data and provide mechanism to specify how to calculate price data given multiple sources. Ultimately, we presume this data will be provided under consensus, but until that time, we provide this tool.

#### Usage

`Usage:`    ethprice [-a|-c|-f|-p|-w|-o|-t|-v|-h]  
`Purpose:`  Freshen and/or display price data for the Ethereum network and other purposes.
             
`Where:`  

| Option | Full Command | Description |
| -------: | :------- | :------- |
| -a | --at | Report the price since the nearest five minutes to :ts (timestamp) |
| -f | --freshen | Freshen database (append new data) |
| -p | --period | Display prices in this increment. Default 120 mins or :t where t is [5&#124;15&#124;30&#124;120&#124;240&#124;1440] |
| -r | --refreshen | Clear the database and refreshen all price data |
| -w | --when | Time of day to start the display. :h determines the hour to start |
| -v | --verbose | set verbose level. Follow with a number to set level (-v0 for silent) |
| -h | --help | display this help screen |

#### Other Options

All QuickBlocks command-line tools support the following commands (although in some case, they have no meaning):

    Command     |         Description
    -----------------------------------------------------------------------------
    --version   |   display the current version of the tool
    --nocolors  |   turn off colored display
    --wei       |   specify value in wei (the default)
    --ether     |   specify value in ether
    --dollars   |   specify value in US dollars
    --file:fn   |   specify multiple sets of command line options in a file.
*For the `--file:fn` option, place a series of valid command lines in a file and use the above option. In some cases, this option may significantly improve performance. Use semi-colon make comments.*

**Powered by QuickBlocks<sup>&reg;<sup>**  
Powered, in part, by Poloniex<sup>&reg;<sup>
