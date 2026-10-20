<?xml version="1.0" encoding="UTF-8"?>
<mxfile host="app.diagrams.net" modified="2026-10-21T00:00:00.000Z" agent="Gemini" version="21.0.0" type="device">
  <diagram id="hoverboard_vesc_fw" name="Hoverboard-VESC STM32F103RCTx Flowchart">
    <mxGraphModel dx="1000" dy="1000" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169" math="0" shadow="0">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- SECTION I -->
        <mxCell id="sec1" value="I. SYSTEM INITIALIZATION &amp; SETUP ROUTINE" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="40" y="20" width="300" height="30" as="geometry" />
        </mxCell>
        <mxCell id="node_start" value="START / RESET" style="ellipse;whiteSpace=wrap;html=1;fontStyle=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="100" y="60" width="140" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_reset_csr" value="Catat Sumber Reset MCU&#xa;boot_reset_csr = RCC-&gt;CSR" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="120" width="220" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_clock" value="HAL_Init() &amp; SystemClock_Config()&#xa;Clock STM32F103 (72 MHz / 64 MHz)" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="180" width="220" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_clock_chk" value="Clock Berhasil?" style="rhombus;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="110" y="240" width="120" height="50" as="geometry" />
        </mxCell>
        <mxCell id="node_periph" value="Inisialisasi Peripheral &amp; Hardware&#xa;MX_GPIO_Init, MX_TIM_Init, MX_ADC1/2_Init" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="310" width="220" height="45" as="geometry" />
        </mxCell>
        <mxCell id="node_adc_start" value="Mulai ADC &amp; Interrupt System&#xa;HAL_ADC_Start() | enable_irq()" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="375" width="220" height="40" as="geometry" />
        </mxCell>

        <!-- SECTION II -->
        <mxCell id="sec2" value="II. MAIN LOOP / TASK SCHEDULER" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="40" y="435" width="300" height="30" as="geometry" />
        </mxCell>
        <mxCell id="node_main_loop" value="while (1) - Loop Utama&#xa;Baca perintah &amp; kondisi sistem" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="60" y="470" width="220" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_cmd_chk" value="Paket Valid &amp; CRC Benar?" style="rhombus;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="100" y="530" width="140" height="50" as="geometry" />
        </mxCell>
        <mxCell id="node_payload" value="Baca Payload &amp; Haluskan Perintah&#xa;rateLimiter16() | filtLowPass32()" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="600" width="220" height="45" as="geometry" />
        </mxCell>

        <!-- SECTION IV -->
        <mxCell id="sec4" value="IV. FAULT HANDLING &amp; SAFETY" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="40" y="665" width="300" height="30" as="geometry" />
        </mxCell>
        <mxCell id="node_fault_chk" value="Fault / Timeout / Cutoff?" style="rhombus;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="100" y="700" width="140" height="50" as="geometry" />
        </mxCell>
        <mxCell id="node_fault_act" value="Matikan Bridge Power Stage&#xa;mc_pwm_for_force_bridges_off()" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="770" width="220" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_housekeeping" value="Outer Control &amp; Housekeeping&#xa;mcpwm_foc_housekeeping_non_isr()" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="60" y="830" width="220" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_off_chk" value="Shutdown Diminta?" style="rhombus;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="105" y="890" width="130" height="50" as="geometry" />
        </mxCell>
        <mxCell id="node_end" value="END / POWER OFF" style="ellipse;whiteSpace=wrap;html=1;fontStyle=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="100" y="960" width="140" height="40" as="geometry" />
        </mxCell>

        <!-- SECTION III -->
        <mxCell id="sec3" value="III. HIGH-FREQUENCY ISR / FOC" style="text;html=1;strokeColor=none;fillColor=none;align=left;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="400" y="20" width="300" height="30" as="geometry" />
        </mxCell>
        <mxCell id="node_isr_trig" value="Trigger: TIM1 / TIM8 Trigger ADC1/2&#xa;DMA1_Channel1_IRQHandler() NVIC=0" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="420" y="60" width="240" height="45" as="geometry" />
        </mxCell>
        <mxCell id="node_offset_chk" value="offsetcount &lt; 2000?" style="rhombus;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="470" y="125" width="140" height="50" as="geometry" />
        </mxCell>
        <mxCell id="node_offset_act" value="Kalibrasi Offset ADC Current&#xa;update_offset() | offsetcount++" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="195" width="240" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_clarke" value="Transformasi Clarke&#xa;foc_clarke_ab_q4(I_a, I_b, I_alpha, I_beta)" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="255" width="240" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_park" value="Transformasi Park&#xa;foc_park_q4(I_alpha, I_beta, theta)" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="315" width="240" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_pi_ctrl" value="Pengendali Arus PI&#xa;Hitung Vd, Vq | Batasi Arus &amp; Vektor" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="375" width="240" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_svpwm" value="Inverse Park &amp; Space Vector PWM&#xa;foc_centered_svpwm(Vd, Vq, theta)" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="435" width="240" height="40" as="geometry" />
        </mxCell>
        <mxCell id="node_pwm_upd" value="Perbarui Register PWM Hardware&#xa;LEFT_TIM / RIGHT_TIM CCR1/2/3" style="rounded=0;whiteSpace=wrap;html=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="420" y="495" width="240" height="45" as="geometry" />
        </mxCell>
        <mxCell id="node_isr_ret" value="ISR RETURN" style="ellipse;whiteSpace=wrap;html=1;fontStyle=1;strokeColor=#000000;fillColor=#ffffff;" vertex="1" parent="1">
          <mxGeometry x="470" y="560" width="140" height="40" as="geometry" />
        </mxCell>

        <!-- EDGES / CONNECTIONS -->
        <mxCell id="e1" edge="1" parent="1" source="node_start" target="node_reset_csr" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e2" edge="1" parent="1" source="node_reset_csr" target="node_clock" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e3" edge="1" parent="1" source="node_clock" target="node_clock_chk" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e4" edge="1" parent="1" source="node_clock_chk" target="node_periph" value="YA" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e5" edge="1" parent="1" source="node_periph" target="node_adc_start" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e6" edge="1" parent="1" source="node_adc_start" target="node_main_loop" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e7" edge="1" parent="1" source="node_main_loop" target="node_cmd_chk" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e8" edge="1" parent="1" source="node_cmd_chk" target="node_payload" value="YA" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e9" edge="1" parent="1" source="node_payload" target="node_fault_chk" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e10" edge="1" parent="1" source="node_fault_chk" target="node_fault_act" value="YA" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e11" edge="1" parent="1" source="node_fault_chk" target="node_housekeeping" value="TIDAK" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e12" edge="1" parent="1" source="node_fault_act" target="node_housekeeping" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e13" edge="1" parent="1" source="node_housekeeping" target="node_off_chk" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e14" edge="1" parent="1" source="node_off_chk" target="node_end" value="YA" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />

        <mxCell id="e15" edge="1" parent="1" source="node_isr_trig" target="node_offset_chk" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e16" edge="1" parent="1" source="node_offset_chk" target="node_offset_act" value="YA" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e17" edge="1" parent="1" source="node_offset_chk" target="node_clarke" value="TIDAK" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e18" edge="1" parent="1" source="node_clarke" target="node_park" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e19" edge="1" parent="1" source="node_park" target="node_pi_ctrl" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e20" edge="1" parent="1" source="node_pi_ctrl" target="node_svpwm" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e21" edge="1" parent="1" source="node_svpwm" target="node_pwm_upd" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
        <mxCell id="e22" edge="1" parent="1" source="node_pwm_upd" target="node_isr_ret" style="edgeStyle=orthogonalEdgeStyle;rounded=0;html=1;strokeColor=#000000;" />
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>