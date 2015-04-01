# magento-multi-maintenance
Allows custom store-specific designs for Magento in installations with multiple stores

## Usage

### Installation
Clone the repository, then copy the content of the "errors" folder into your Magento installation.
To add store-specific maintenance pages, create a [mage_run_code].design.xml file, and a [mage_run_code] folder based off the "errors/default" folder. (if your Magento store's run code is "coolstore" you'd create "coolstore.design.xml" and a folder "coolstore" in the "errors" directory).

### The code
To make this possible, the following modifications were made to Magento's "error/processor.php" file in the "_prepareConfig()" method.
``` php
        $designXml = self::MAGE_ERRORS_DESIGN_XML;
        $runCode = isset($_SERVER['MAGE_RUN_CODE']) ? $_SERVER['MAGE_RUN_CODE'] : 'base';
        if($runCode) {
            $runCode = str_replace('_staging', '', $runCode);
            if($this->_getFilePath($runCode . '.design.xml')) {
                $designXml = $runCode . '.design.xml';
            }
        }
        $design = $this->_loadXml($designXml);
```