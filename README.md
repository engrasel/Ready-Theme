/**
 * Register Google Fonts
 */
function ready_fonts_url() {
	$fonts_url = '';

	$Montserrat = _x( 'on', 'Montserrat font: on or off', 'theme-slug' );
	$Raleway 	= _x( 'on', 'Raleway font: on or off', 'theme-slug' );
	$Halant 	= _x( 'on', 'Halant font: on or off', 'theme-slug' );
	 
	if ( 'off' !== $Montserrat || 'off' !== $Raleway || 'off' !== $Halant ) {
	$font_families = array();
	 
	if ( 'off' !== $Montserrat ) {
	$font_families[] = 'Montserrat:400,700';
	}
	 
	if ( 'off' !== $Raleway ) {
	$font_families[] = 'Raleway:300,400,500';
	}

	if ( 'off' !== $Raleway ) {
	$font_families[] = 'Halant:300,400';
	}
	 
	$query_args = array(
    'family' => urlencode( implode( '|', $font_families ) ),
    'subset' => urlencode( 'latin,latin-ext' ),
	);
	 
	$fonts_url = add_query_arg( $query_args, 'https://fonts.googleapis.com/css' );
	return esc_url_raw( $fonts_url );

	}
}


/**
 * Enqueue scripts and styles.
 */
function ready_scripts() {
   wp_enqueue_style( 'google-fonts', ready_fonts_url(), array(), null );
}
add_action( 'wp_enqueue_scripts', 'ready_scripts' );
