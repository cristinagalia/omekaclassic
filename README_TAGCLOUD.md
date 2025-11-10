# omekaclassic
Plugin for omeka to show tagcloud

<?php
  
class TagsCloudCrisandCrisPlugin extends Omeka_Plugin_AbstractPlugin
{
    protected $_hooks = [
        'initialize',
    ];

    public function hookInitialize()
    {
        add_shortcode('tagscloud', [$this, 'tagsCloudShortcode']);
    }

    public function tagsCloudShortcode($args, $view)
    {

 $tags = get_db()->getTable('Tag')->findBy(array('type'=>'Item'));
$output = tag_cloud($tags, 'items/browse');


   return $output;
    }
}

