# STM32F401CCU6_USB_Data
Send string and integer through USB

#include "main.h"
#include "usb_device.h"

/* Private includes ----------------------------------------------------------*/
/* USER CODE BEGIN Includes */
#include "usbd_cdc_if.h"
#include "string.h"
#include "stdint.h"
/* USER CODE END Includes */


/* USER CODE BEGIN PV */
char msg[200];
uint8_t count=0;
/* USER CODE END PV */

/* USER CODE BEGIN WHILE */
  while (1)
  {sprintf(msg, "Hello %d\r\n", count);

	CDC_Transmit_FS((uint8_t*) msg, strlen(msg));
	HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_13);
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
	HAL_Delay(1000);
	count++;

	if (count>10)
	{
		count=0;
	}
  }
  /* USER CODE END 3 */
