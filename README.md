<?xml version="1.0" encoding="UTF-8"?>
<parse-tree>
  <node name="S">
    <leaf value="fun" />
    <leaf value="calc" type="id" />
    <leaf value="(" />
    <node name="P">
      <node name="param">
        <leaf value="a" type="id" />
        <leaf value=":" />
        <leaf value="Int" type="T" />
      </node>
      <leaf value="," />
      <node name="P">
        <node name="param">
          <leaf value="b" type="id" />
          <leaf value=":" />
          <leaf value="Int" type="T" />
        </node>
        <leaf value="," />
        <node name="P">
          <node name="param">
            <leaf value="c" type="id" />
            <leaf value=":" />
            <leaf value="Int" type="T" />
          </node>
        </node>
      </node>
    </node>
    <leaf value=")" />
    <leaf value=":" />
    <leaf value="Int" type="T" />
    <leaf value="{" />
    <leaf value="return" />
    <node name="E">
      <node name="E">
        <leaf value="a" type="id" />
      </node>
      <leaf value="+" />
      <node name="E">
        <leaf value="(" />
        <node name="E">
          <node name="E">
            <leaf value="b" type="id" />
          </node>
          <leaf value="*" />
          <node name="E">
            <leaf value="c" type="id" />
          </node>
        </node>
        <leaf value=")" />
      </node>
    </node>
    <leaf value="}" />
    <leaf value=";" />
  </node>
</parse-tree>
