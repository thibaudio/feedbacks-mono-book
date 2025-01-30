# API Reference

## POST https://api.bugbee.app/v1/report
Create a report for game, with an optional attachment.

### Header
Content-Type: multipart/form-data; boudary=\<boundary word\>  
Content-Length: \<size of the body\> 

### Body
#### game_id - string - Required
Game ID returned by the `/add_endpoint_integration` command.
#### endpoint_secret - string - Required
The `shared_code` used when register a channel with the `/add_endpoint_integration` command.
#### description - string - Required
The content of the report written by the user.
#### report_type - string - Required
The type of report that is being created, can be Feedback or Bug.
#### attachment - bytes - Optional
Needed if attachment_filename is set.
The binary array containing the raw data of the file to upload.
#### attachment_filename - bytes - Optional
Needed if attachment is set.  
The name of the file uploaded in the attachment field.

### Example
A simple Godot Example: 
```GDScript
func send_feedback_multipart(game_id: String, endpoint_secret: String, text: String, report_type: String, image: Image) -> void:
	var http_request = HTTPRequest.new()
	add_child(http_request)

	var body = PackedByteArray()
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"attachment\"\r\n".to_utf8_buffer())
	body.append_array("Content-Type: image/png\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array(image.save_png_to_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"game_id\"\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array(game_id.to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"endpoint_secret\"\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array(endpoint_secret.to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"description\"\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array(text.to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"report_type\"\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array(report_type.to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary".to_utf8_buffer())
	body.append_array("\r\nContent-Disposition: form-data; name=\"attachment_filename\"\r\n".to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("screenshot-{0}.png".format([Time.get_datetime_string_from_system()]).to_utf8_buffer())
	body.append_array("\r\n".to_utf8_buffer())
	body.append_array("--boundary--".to_utf8_buffer())
	
	var headers = [
		"Content-Length: " + str(body.size()),
		"Content-Type: multipart/form-data; boundary=boundary"
		]
	
	http_request.request_raw("https://api.bugbee.app/v1/report", headers, HTTPClient.METHOD_POST, body)
```
