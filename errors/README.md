# magento-multi-maintenance
Allows custom store-specific designs for Magento in installations with multiple stores

## Installation
Copy
        $designXml = self::MAGE_ERRORS_DESIGN_XML;
        $runCode = isset($_SERVER['MAGE_RUN_CODE']) ? $_SERVER['MAGE_RUN_CODE'] : 'base';
        if($runCode) {
            $runCode = str_replace('_staging', '', $runCode);
            if($this->_getFilePath($runCode . '.design.xml')) {
                $designXml = $runCode . '.design.xml';
            }
        }
        $design = $this->_loadXml($designXml);
