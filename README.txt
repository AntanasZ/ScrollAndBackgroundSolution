Scroll Solution:
World.cpp{
	line 12: changed to "m_world_bounds(0.f, 0.f, 2000.f, m_camera.getSize().y)"
	line 26: changed to "m_camera.move(-m_scrollspeed * dt.asSeconds(), 0);"
	line 106: in BuildScene(), added code to rotate player 90 degrees "m_player_aircraft->setRotation(90.f);"
	line 151: in AdaptPlayerVelocity(), changed to "m_player_aircraft->Accelerate(-m_scrollspeed, 0.f);" 
}

Background Solution:
World.hpp{
	line 37: Added new method UpdateBackground()
	line 50: Added a m_counter variable
}

World.cpp{
	line 40: in Update(), added a call to UpdateBackground()
	line 43: Added implementation of UpdateBackground() method

	UpdateBackground() constanly increments m_counter and checks if it reaches a value >= 1500.
	Once m_counter is above 1500, world bounds width is increased by 2000 and counter is reset to 0.
	The background is prepared again and atttached to m_scene_layer like in BuildScene().
	Since background sprite is a unique ptr, i wasnt sure how to detach old background sprite from scene layers
}