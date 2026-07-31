# STM32-School-


USART_Print : printf 시리얼 디버깅
터미널 통신 프로그램 설치 : [https://github.com/TeraTermProject/teraterm/releases?authuser=0]
<img width="363" height="326" alt="image" src="https://github.com/user-attachments/assets/7decd6e5-421a-4a2e-8ab4-f1c0251479f2" />
<img width="999" height="655" alt="image" src="https://github.com/user-attachments/assets/e5af3f51-fcea-4133-a74c-ffc42708bc01" />



/* USER CODE BEGIN 0 */
#ifdef __GNUC__
/* With GCC, small printf (option LD Linker->Libraries->Small printf
   set to 'Yes') calls __io_putchar() */
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#else
#define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#endif /* __GNUC__ */

/**
  * @brief  Retargets the C library printf function to the USART.
  * @param  None
  * @retval None
  */
PUTCHAR_PROTOTYPE
{
  /* Place your implementation of fputc here */
  /* e.g. write a character to the USART1 and Loop until the end of transmission */
  if (ch == '\n')
    HAL_UART_Transmit (&huart2, (uint8_t*) "\r", 1, 0xFFFF);
  HAL_UART_Transmit (&huart2, (uint8_t*) &ch, 1, 0xFFFF);

  return ch;
}
