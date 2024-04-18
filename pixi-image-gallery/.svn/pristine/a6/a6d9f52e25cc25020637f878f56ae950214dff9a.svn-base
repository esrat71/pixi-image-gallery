<?php
namespace Pixi_Image_Gallery;

if ( ! defined( 'ABSPATH' ) ) {
	exit; // Exit if accessed directly.
}

/**
 * Elementor Widget 2.
 *
 * Elementor widget that inserts an embbedable content into the page, from any given URL.
 *
 * @since 1.0.0
 */
class pixi_image_gallery_lite extends \Elementor\Widget_Base {

	/**
	 * Get widget name.
	 *
	 * Retrieve widget name.
	 *
	 */
	public function get_name() {
		return 'pixi-img-gallery';
	}

	/**
	 * Get widget title.
	 *
	 * Retrieve  widget title.
	 */
	public function get_title() {
		return esc_html__( 'Pixi Image Gallery', 'pixi-image-gallery' );
	}

	/**
	 * Get widget icon.
	 *
	 * Retrieve  widget icon.
	 *
	 */
	public function get_icon() {
		return 'eicon-gallery-grid';
	}


	/**
	 * Get widget categories.
	 *
	 * Retrieve the list of categories the  widget belongs to.
	 *
	 */
	public function get_categories() {
		return [ 'pixi-category' ];
	}


	/**
	 * Get widget style depends
	 *
	 * Retrieve the list of categories the  widget belongs to.
	 *
	 */


	public function get_style_depends() {
		return [
			'gallery-common-style',
			'bootstrap',
		];
	}
	
	

	/**
	 * Register  widget controls.
	 *
	 * Add input fields to allow the user to customize the widget settings.

	 */
	protected function register_controls() {

		$this->start_controls_section(
			'content_section',
			[
				'label' => esc_html__( 'Content', 'pixi-image-gallery' ),
				'tab' => \Elementor\Controls_Manager::TAB_CONTENT,
			]
		);


		$this->add_control(
			'hover_effects_style',
			[
				'label' => esc_html__( 'Hover Effects', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => 'default',
				'options' => [
					'default'  => esc_html__( 'Default', 'pixi-image-gallery' ),
					'zoomIn'  => esc_html__( 'Zoom In', 'pixi-image-gallery' ),
					'shrink' => esc_html__( 'Shrink', 'pixi-image-gallery' ),
					'zoomLeft' => esc_html__( 'Zoom Left', 'pixi-image-gallery' ),
				],
			]
		);


	

		$this->add_control(
			'column_option',
			[
				'label' => esc_html__( 'Column', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => '3',
				'options' => [
					'1' => esc_html__( '1', 'pixi-image-gallery' ),
					'2' => esc_html__( '2', 'pixi-image-gallery' ),
					'3' => esc_html__( '3', 'pixi-image-gallery' ),
					'4' => esc_html__( '4', 'pixi-image-gallery' ),
					'5'  => esc_html__( '5', 'pixi-image-gallery' ),
					'6'  => esc_html__( '6', 'pixi-image-gallery' ),
				],
			]
		);

		$this->add_control(
			'column_gap',
			[
				'label' => esc_html__( 'Columns Gap', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => 'default',
				'options' => [
					'default'  => esc_html__( 'Default', 'pixi-image-gallery' ),
					'g-custom' => esc_html__( 'Custom', 'pixi-image-gallery' ),
				],
			]
		);

		$this->add_responsive_control(
			'content_item_spacing',
			[
				'label' => esc_html__( 'Spacing', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SLIDER,
				'size_units' => [ 'px'],
				'selectors' => [
					'{{WRAPPER}} .pixi-portfolio .pixi-inner-item' => 'margin-bottom: {{SIZE}}{{UNIT}};',
				],
			]
		);
		
		$this->add_responsive_control(
			'custom_column_gap',
			[
				'label' => esc_html__( 'Custom Column Gap', 'eduhash-toolkit' ),
				'type' => \Elementor\Controls_Manager::SLIDER,
				'size_units' => [ 'px', '%' ],
				'default' => [
					'unit' => 'px',
					'size' => 0,
				],
				'condition' => [
					'column_gap' => 'g-custom',
				],
				'selectors' => [
					'{{WRAPPER}} .pixi-gallery-wrapper .gallery-inner ' => 'margin-bottom: -{{SIZE}}{{UNIT}}; margin-right: -{{SIZE}}{{UNIT}};',
					'{{WRAPPER}} .pixi-gallery-wrapper .pixi-inner-item' => 'padding-right: {{SIZE}}{{UNIT}}; padding-bottom: {{SIZE}}{{UNIT}};',
				],
			]
		);

		$this->add_responsive_control(
			'column_display',
			[
				'label' => esc_html__( 'Display', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => 'flex',
				'options' => [
					'default' => esc_html__( 'None', 'pixi-image-gallery' ),
					'block' => esc_html__( 'Block', 'pixi-image-gallery' ),
					'flex' => esc_html__( 'Flex', 'pixi-image-gallery' ),
				],
				'selectors' => [
					'{{WRAPPER}} .pixi-gallery-wrapper .gallery-inner ' => 'display: {{UNIT}};',
				],
			]
		);

		$this->add_control(
			'column_align',
			[
				'label' => esc_html__( 'Vertical Align', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => 'center',
				'options' => [
					'none' => esc_html__( 'None', 'pixi-image-gallery' ),
					'start' => esc_html__( 'Top', 'pixi-image-gallery' ),
					'center' => esc_html__( 'Center', 'pixi-image-gallery' ),
					'end' => esc_html__( 'Bottom', 'pixi-image-gallery' ),
				],
				'selectors' => [
					'{{WRAPPER}} .pixi-gallery-wrapper .gallery-inner ' => 'align-items: {{UNIT}};',
				],
			]
		);

		// Repeater Start

		$repeater = new \Elementor\Repeater();

		$repeater->add_control(
			'widget_image',
			[
				'label' => esc_html__( 'Choose Image', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::MEDIA,
				'default' => [
					'url' => \Elementor\Utils::get_placeholder_image_src(),
				],
			]
		);


		$repeater->add_control(
			'link_option',
			[
				'label' => esc_html__( 'Link', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SELECT,
				'default' => 'media',
				'options' => [
					'media'  => esc_html__( 'Media File', 'pixi-image-gallery' ),
					'custom' => esc_html__( 'Custom Link', 'pixi-image-gallery' ),
				],
			]
		);

		$repeater->add_control(
			'widget_link',
			[
				'label' => esc_html__( 'Link', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::URL,
				'placeholder' => esc_html__( 'https://your-link.com', 'pixi-image-gallery' ),
				'default' => [
					'url' => '',
					'is_external' => true,
					'nofollow' => true,
				],
				'condition' => array(
					'link_option' => ['custom'],
				)
			]
		);
		

		$this->add_control(
			'gallery_lists',
			[
				'label' => __( 'Gallery Images', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::REPEATER,
				'fields' => $repeater->get_controls(),
				'default' => [
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],
					[
						'widget_image' => [
							'url' => \Elementor\Utils::get_placeholder_image_src(),
						],
					],

				],
			]
		);

		// Repeater End



		$this->end_controls_section();


		//  STyle controls

		$this->start_controls_section(
			'img_style_section',
			[
				'label' => esc_html__( 'Image', 'pixi-image-gallery' ),
				'tab' => \Elementor\Controls_Manager::TAB_STYLE,
			]
		);

		$this->add_control(
			'img_width',
			[
				'label' => esc_html__( 'Width', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::SLIDER,
				'size_units' => [ 'px', '%' ],
				'range' => [
					'px' => [
						'min' => 0,
						'max' => 1000,
						'step' => 5,
					],
					'%' => [
						'min' => 0,
						'max' => 100,
					],
				],
				'default' => [
					'unit' => '%',
					'size' => 100,
				],
				'selectors' => [
					'{{WRAPPER}} .pixi-inner-item img' => 'width: {{SIZE}}{{UNIT}};',
				],
			]
		);

		$this->add_control(
			'image_radius',
			[
				'label' => esc_html__( 'Border radius', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::DIMENSIONS,
				'size_units' => [ 'px', '%', 'em' ],
				'selectors' => [
					'{{WRAPPER}} .pixi-inner-item img' => 'border-radius: {{TOP}}{{UNIT}} {{RIGHT}}{{UNIT}} {{BOTTOM}}{{UNIT}} {{LEFT}}{{UNIT}};',
				],
			]
		);

		$this->add_group_control(
			\Elementor\Group_Control_Border::get_type(),
			[
				'name' => 'img_border',
				'label' => __( 'Border', 'pixi-image-gallery' ),
				'selector' => '{{WRAPPER}}  .pixi-inner-item img',
			]
		);

		$this->end_controls_section();


		// content Style

		$this->start_controls_section(
			'content_style_section',
			[
				'label' => esc_html__( 'Content Item', 'pixi-image-gallery' ),
				'tab' => \Elementor\Controls_Manager::TAB_STYLE,
			]
		);

		$this->add_group_control(
			\Elementor\Group_Control_Border::get_type(),
			[
				'name' => 'item_border',
				'label' => __( 'Border', 'pixi-image-gallery' ),
				'selector' => '{{WRAPPER}}  .pixi-inner-item',
			]
		);

		$this->add_group_control(
			\Elementor\Group_Control_Box_Shadow::get_type(),
			[
				'name' => 'item_box_shadow',
				'label' => __( 'Box Shadow', 'pixi-image-gallery' ),
				'selector' => '{{WRAPPER}} .pixi-inner-item',
			]
		);

		$this->add_control(
			'content_bg_color',
			[
				'label' => esc_html__( 'Background Color', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::COLOR,
				'selectors' => [
					'{{WRAPPER}} .pixi-inner-item' => 'background: {{VALUE}}',
				],
			]
		);

		$this->add_control(
			'content_padding',
			[
				'label' => esc_html__( 'Padding', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::DIMENSIONS,
				'size_units' => [ 'px', '%', 'em' ],
				'selectors' => [
					'{{WRAPPER}} .pixi-inner-item' => 'padding: {{TOP}}{{UNIT}} {{RIGHT}}{{UNIT}} {{BOTTOM}}{{UNIT}} {{LEFT}}{{UNIT}};',
				],
			]
		);

		$this->add_control(
			'content_radius',
			[
				'label' => esc_html__( 'Border radius', 'pixi-image-gallery' ),
				'type' => \Elementor\Controls_Manager::DIMENSIONS,
				'size_units' => [ 'px', '%', 'em' ],
				'selectors' => [
					'{{WRAPPER}} .pixi-inner-item' => 'border-radius: {{TOP}}{{UNIT}} {{RIGHT}}{{UNIT}} {{BOTTOM}}{{UNIT}} {{LEFT}}{{UNIT}};',
				],
			]
		);

		$this->end_controls_section();

	}

	/**
	 * Render  widget output on the frontend.
	 *
	 * Written in PHP and used to generate the final HTML.
	 *
	 * @since 1.0.0
	 * @access protected
	 */
	protected function render() {

		$settings = $this->get_settings_for_display();

		$hover_effects_style = $settings['hover_effects_style'];

		if('zoomIn' == $hover_effects_style){
			$effect= "zoomIn";
		}
		elseif('shrink' == $hover_effects_style){
			$effect= "shrink";
		}
		elseif('zoomLeft' == $hover_effects_style){
			$effect= "zoomLeft";
		}
		else{
			$effect="";
		}

		?>
		<div class="pixi-gallery-wrapper">
			<div class="gallery-inner gallery-columns-<?php echo esc_attr($settings['column_option']); ?> ">
				<?php foreach($settings['gallery_lists'] as $gallery_item){ ?>
					<div class="pixi-inner-item elementor-repeater-item-<?php echo esc_attr( $gallery_item['_id'] )?>">
						<?php if ('media' == $gallery_item['link_option'] ){ ?>
							<a data-gall="pixiGallery"  class="port_popup img-fluid" href="<?php echo esc_url($gallery_item['widget_image']['url'],'pixi-image-gallery');?>">
						<?php } else { ?>
							<a target="_blank" href="<?php echo esc_url($gallery_item['widget_link']['url'],'pixi-image-gallery');?>">
						<?php } ?>
							<div class="<?php echo esc_attr($effect,'pixi-image-gallery');?>">
								<img src="<?php echo esc_url($gallery_item['widget_image']['url'],'pixi-image-gallery');?>" 
								alt="<?php the_title_attribute()?>"  class="img-fluid">
							</div>
						</a>
					</div>
				<?php } ?>
			</div>
		</div>

			
	


		<?php 

	}

}
