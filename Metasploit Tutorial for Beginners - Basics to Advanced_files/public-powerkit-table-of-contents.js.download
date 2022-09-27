/**
 * Table of Contents
 */
( function( $ ) {

	$( document ).ready( function() {

		var pk_toc_container  = '.entry-content';
		var pk_toc_wpadminbar = 0;
		var pk_toc_offset     = 80;

		// Get height adminbar.
		if ( $( '#wpadminbar' ).length > 0 ) {
			pk_toc_wpadminbar = $( '#wpadminbar' ).outerHeight();

			if ( 'absolute' === $( '#wpadminbar' ).css( 'position' ) ) {
				pk_toc_wpadminbar = 0;
			}
		}

		/**
		 * TOC: Click hide.
		 */
		$( document ).on( 'click', '.pk-toc-btn-hide', function() {

			if ( $( this ).closest( '.pk-toc' ).hasClass( 'pk-toc-hide' ) ) {
				$( this ).closest( '.pk-toc' ).removeClass( 'pk-toc-hide' );

				$( this ).html( powerkit_toc_config.label_hide );

				$( this ).closest( '.pk-toc' ).find('> ol, > ul').slideDown(200, function(){
					$( this ).animate({opacity: 1}, 150, 'swing');
				});
			} else {
				$( this ).closest( '.pk-toc' ).addClass( 'pk-toc-hide' );

				$( this ).html( powerkit_toc_config.label_show );

				$( this ).closest( '.pk-toc' ).find('> ol, > ul').animate({opacity: 0}, 150, 'swing', function(){
					$( this ).slideUp(200);
				});
			}
		} );

		/**
		 * TOC: Scroll to Heading.
		 */
		$( document ).on( 'click', '.pk-toc a', function() {

			var objContent = $( pk_toc_container );

			// If the list is found inside the content.
			if ( $( this ).closest( pk_toc_container ).length > 0 ) {
				objContent = $( this ).closest( pk_toc_container );
			}

			// Get position heading.
			var offsetHeading = $( objContent ).find( $( this ).attr( 'href' ) ).offset();

			if ( typeof offsetHeading === 'undefined' ) {
				return;
			}

			var positionHeading = offsetHeading.top;

			// Scroll to Heading.
			$( 'body, html' ).animate( {
				scrollTop: positionHeading - pk_toc_wpadminbar - pk_toc_offset
			}, 400 );

			return false;
		} );

		/**
		 * TOC: Active element of toc widget.
		 */
		$( window ).scroll( function() {
			var scrollTop = $( window ).scrollTop();

			$( '.powerkit_toc_widget' ).first().find( '.pk-toc a' ).each( function( index, elem ) {

				// Get position heading.
				var offsetHeading = $( $( elem ).attr( 'href' ) ).offset();

				if ( typeof offsetHeading === 'undefined' ) {
					return;
				}

				var positionHeading = offsetHeading.top;

				if ( positionHeading - scrollTop - pk_toc_wpadminbar - pk_toc_offset <= 0 ) {
					var filterElem = '[href="%1s"]'.replace( '%1s', $( elem ).attr( 'href' ) );

					// Find menu element.
					var menuElem = $( '.powerkit_toc_widget .pk-toc' ).find( 'a' ).filter( filterElem );

					// Remove class active.
					$( '.powerkit_toc_widget .pk-toc li' ).removeClass( 'active active-child' );

					// Add class active.
					$( menuElem ).parents( 'li' ).addClass( 'active-child' );
					$( menuElem ).parent( 'li' ).addClass( 'active' );
				}
			} );
		} );

	} );

} )( jQuery );
