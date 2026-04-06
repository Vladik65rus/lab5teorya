    <!-- FunctionDeclNode -->
    <mxCell id="func" value="FunctionDeclNode" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;fontSize=14;" vertex="1" parent="1">
      <mxGeometry x="300" y="20" width="160" height="40" as="geometry"/>
    </mxCell>
    
    <!-- name -->
    <mxCell id="name" value="name: &quot;calc&quot;" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="100" y="90" width="120" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge1" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="func" target="name">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- return_type -->
    <mxCell id="ret_type" value="return_type: Int" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="300" y="90" width="130" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge2" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="func" target="ret_type">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- parameters label -->
    <mxCell id="params_label" value="parameters:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontStyle=1;" vertex="1" parent="1">
      <mxGeometry x="500" y="90" width="100" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge3" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="func" target="params_label">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- a: Int -->
    <mxCell id="param_a" value="a: Int" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="460" y="150" width="80" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge4" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="params_label" target="param_a">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- b: Int -->
    <mxCell id="param_b" value="b: Int" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="520" y="150" width="80" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge5" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="param_a" target="param_b">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- c: Int -->
    <mxCell id="param_c" value="c: Int" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="580" y="150" width="80" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge6" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="param_b" target="param_c">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- body label -->
    <mxCell id="body_label" value="body:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontStyle=1;" vertex="1" parent="1">
      <mxGeometry x="300" y="160" width="80" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge7" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="func" target="body_label">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- ReturnStmtNode -->
    <mxCell id="return_stmt" value="ReturnStmtNode" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontStyle=1;" vertex="1" parent="1">
      <mxGeometry x="280" y="220" width="130" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge8" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="body_label" target="return_stmt">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- expression label -->
    <mxCell id="expr_label" value="expression:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="280" y="290" width="90" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge9" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="return_stmt" target="expr_label">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- BinaryOpNode + -->
    <mxCell id="binary_plus" value="BinaryOpNode: +" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="1">
      <mxGeometry x="270" y="350" width="140" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge10" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="expr_label" target="binary_plus">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- left label -->
    <mxCell id="left_label" value="left:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="140" y="420" width="70" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge11" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="binary_plus" target="left_label">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- IdentifierNode a -->
    <mxCell id="id_a" value="IdentifierNode: a" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="120" y="480" width="130" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge12" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="left_label" target="id_a">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- right label -->
    <mxCell id="right_label" value="right:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="430" y="420" width="70" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge13" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="binary_plus" target="right_label">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- BinaryOpNode * -->
    <mxCell id="binary_mul" value="BinaryOpNode: *" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontStyle=1;" vertex="1" parent="1">
      <mxGeometry x="420" y="480" width="130" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge14" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="right_label" target="binary_mul">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- left of * -->
    <mxCell id="left_label_mul" value="left:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="330" y="550" width="70" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge15" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="binary_mul" target="left_label_mul">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- IdentifierNode b -->
    <mxCell id="id_b" value="IdentifierNode: b" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="310" y="610" width="130" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge16" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="left_label_mul" target="id_b">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- right of * -->
    <mxCell id="right_label_mul" value="right:" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="530" y="550" width="70" height="30" as="geometry"/>
    </mxCell>
    <mxCell id="edge17" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="binary_mul" target="right_label_mul">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- IdentifierNode c -->
    <mxCell id="id_c" value="IdentifierNode: c" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="510" y="610" width="130" height="40" as="geometry"/>
    </mxCell>
    <mxCell id="edge18" style="edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;" edge="1" parent="1" source="right_label_mul" target="id_c">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
