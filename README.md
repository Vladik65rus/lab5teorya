<?xml version="1.0" encoding="UTF-8"?>
<parse_tree input="fun calc(a: Int, b: Int, c: Int): Int { return a + (b * c) };">
  <node name="S">
    <leaf>fun</leaf>
    <leaf type="id">calc</leaf>
    <leaf>(</leaf>
    
    <node name="P">
      <leaf type="id">a</leaf>
      <leaf>:</leaf>
      <node name="T">
        <leaf>Int</leaf>
      </node>
      <leaf>,</leaf>
      
      <node name="P">
        <leaf type="id">b</leaf>
        <leaf>:</leaf>
        <node name="T">
          <leaf>Int</leaf>
        </node>
        <leaf>,</leaf>
        
        <node name="P">
          <leaf type="id">c</leaf>
          <leaf>:</leaf>
          <node name="T">
            <leaf>Int</leaf>
          </node>
        </node>
      </node>
    </node>
    
    <leaf>)</leaf>
    <leaf>:</leaf>
    
    <node name="T">
      <leaf>Int</leaf>
    </node>
    
    <leaf>{</leaf>
    <leaf>return</leaf>
    
    <node name="E">
      <node name="E">
        <leaf type="id">a</leaf>
      </node>
      <leaf>+</leaf>
      <node name="E">
        <leaf>(</leaf>
        <node name="E">
          <node name="E">
            <leaf type="id">b</leaf>
          </node>
          <leaf>*</leaf>
          <node name="E">
            <leaf type="id">c</leaf>
          </node>
        </node>
        <leaf>)</leaf>
      </node>
    </node>
    
    <leaf>}</leaf>
    <leaf>;</leaf>
  </node>
</parse_tree>
