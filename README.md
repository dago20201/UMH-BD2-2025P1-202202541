DELIMITER //

CREATE PROCEDURE sp_up_currency(
    IN p_tasa DECIMAL(15,6),
    IN p_currency_id INT
)
BEGIN
    IF p_tasa IS NOT NULL AND p_tasa > 0 AND p_currency_id > 0 THEN
        UPDATE db_demo.currencies 
        SET exchange_rate = p_tasa
        WHERE currency_id = p_currency_id;
        COMMIT;
    ELSE 
        SELECT 'No se realizó ninguna actualización. Verifique los valores ingresados.' AS mensaje;
    END IF;
END //
