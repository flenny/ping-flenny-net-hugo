+++
comments = true
date = "2016-02-17T18:24:49+01:00"
description = "Learn about the reason DataTriggers might not work as they should."
draft = false
image = "images/post/default-post.png"
tags = [".net", "wpf", "xaml"]
title = "Toggle WPF control visibility with DataTriggers"
+++

A frequent source of error while working with triggers is that I set the default value directly on the control itself (e.g. Label). Now when trying to change the value with a trigger that unfortunately won't work. **The default value has to be set in the control's style** as shown in the example below.

~~~aspnet
<Window x:Class="FlennyNET.Examples.DataTrigger.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="DataTrigger Example" Height="350" Width="525">
    <Grid>
        <StackPanel Orientation="Horizontal">
            <Label Content="DataTrigger Example">
                <Label.Style >
                    <Style TargetType="Label">
                        <Setter Property="Visibility" Value="Hidden" />
                        <Style.Triggers>
                            <DataTrigger Binding="{Binding HasValue}" Value="true">
                                <Setter Property="Visibility" Value="Visible" />
                            </DataTrigger>
                        </Style.Triggers>
                    </Style>
                </Label.Style>
            </Label>
        </StackPanel>
    </Grid>
</Window>
~~~