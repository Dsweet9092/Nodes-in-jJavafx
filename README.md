# Nodes-in-jJavafx
Practicing creating a simple node interface.


package nodeplacer;


import javafx.application.Application;
import javafx.concurrent.Task;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.*;
import javafx.scene.input.MouseEvent;
import javafx.scene.layout.HBox;
import javafx.scene.layout.Pane;
import javafx.scene.layout.StackPane;
import javafx.scene.paint.Color;
import javafx.scene.shape.Circle;
import javafx.scene.control.TextArea;

import javafx.stage.Stage;


public class NodePlacer extends Application {
    
    
    private double xpos;
    private double ypos;
    private int count;
    private boolean canPlace = true;
    private boolean place2 = false;
    private boolean place3 = false;
    private boolean icount = true;
    private int i;
    private StackPane root = new StackPane();
    private Label label = new Label("voltage");
    private HBox hbox = new HBox();
    private TextField[] textField = new TextField[6];
    private ToggleButton link1;
    private ToggleButton link2;
    private Button[] button2 = new Button[6];
    private int num;
    private String[] str = new String[6];
    private TextArea textArea;
    
    
    @Override
    public void start(Stage stage) {
        
        // used to add 'voltage' button
        Button btn = new Button();
        btn.setTranslateX(-200);
        btn.setTranslateY(-200);
        
        // specs for the textarea
        textArea = new TextArea();
        textArea.setPrefWidth(25);
        textArea.setMinWidth(20);
        textArea.setMaxWidth(80);
        textArea.setMinHeight(20);
        textArea.setMaxHeight(60);
        textArea.setPrefHeight(30);
        textArea.setEditable(false);
        textArea.setTranslateX(0);
        textArea.setTranslateY(60);

        Scene scene = new Scene(root, 640, 480);
        
        // mouse click event to creat 'voltage' button
        scene.setOnMousePressed(new EventHandler<MouseEvent>(){
            
            public void handle(MouseEvent e) {
                
                // checks if node can be placed
                if (canPlace == true && count >= 1) {
                
                    // stores mouse X and Y click coordinance
                    xpos = e.getX();
                    ypos = e.getY();
                
                    // used for limiting node placements
                    count -= 1;
                    
                    System.out.println("Mouse Pressed at " + xpos + " , " + ypos);
                    icount = true;
                    button2[i] = new Button("Calculate");       // Button array to store individual button information
                    Label label1 = new Label("Voltage");
                    // textfield array for individual information storage
                    textField[i] = new TextField();
                    textField[i].setPrefWidth(25);
                    textField[i].setMinWidth(20);
                    textField[i].setMaxWidth(80);
                    // places each button, label and textfield at unique mouse click locations
                    button2[i].setTranslateX(xpos - 320);
                    button2[i].setTranslateY(ypos - 260);
                    
                    label1.setTranslateX(xpos - 320);
                    label1.setTranslateY(ypos - 240);
                    textField[i].setTranslateX(xpos -320);
                    textField[i].setTranslateY(ypos - 280);
                    // link1 used for future linkage script between nodes
                    link1 = new ToggleButton("Link");
                    link1.setTranslateX(xpos - 260);
                    link1.setTranslateY(ypos - 260);
                    // places all elements inside window
                    root.getChildren().addAll(label1,textField[i],
                                                button2[i],link1);
                
                    // checks number of nodes created and limits them to 6
                if (i <= 6) {
                    button2[i].setOnAction(new EventHandler<ActionEvent>() {
            
                        // sets all initial buttons' information and stores inside array
                    @Override
                    public void handle(ActionEvent event) {
            
                        str[i] = textField[i].getText();
                        textArea.setText(str[i]);
                        
                        // used for debugging
                        System.out.println("Button2 Pressed " + str[i] + " " + i);
                        System.out.println("Button2 Pressed " + str[1] + " " );
                        System.out.println("Button2 Pressed " + str[2] + " " );
                    }
        }); 
                    /* all node information is individual and can be altered
                    with following buttons and textfields.
                    */
                    
                    if (i == 1) {
                    button2[1].setOnAction(new EventHandler<ActionEvent>() {
            
                    @Override
                    public void handle(ActionEvent event) {
                
                        str[1] = textField[1].getText();
                        textArea.setText(str[1]);
                        
                        // used for debugging
                        System.out.println("Button2 Pressed... " + str[1] + " " );
                        System.out.println("Button2 Pressed';'; " + str[2] + " " );
                    }
                }); 
                    
                    }
                    
                    if (i == 2) {
                    button2[2].setOnAction(new EventHandler<ActionEvent>() {
            
                    @Override
                    public void handle(ActionEvent event) {
                
                        str[2] = textField[2].getText();
                        textArea.setText(str[2]);

                    }
                }); 
                    
                    }
                    
                    if (i == 3) {
                    button2[3].setOnAction(new EventHandler<ActionEvent>() {
            
                    @Override
                    public void handle(ActionEvent event) {
                
                        str[3] = textField[3].getText();
                        textArea.setText(str[3]);
                        
                    }
                }); 
                    
                    }
                                        
                    if (i == 4) {
                    button2[4].setOnAction(new EventHandler<ActionEvent>() {
            
                    @Override
                    public void handle(ActionEvent event) {
                
                        str[4] = textField[4].getText();
                        textArea.setText(str[4]);
                        
                    }
                }); 
                    
                    }
                                        
                if (i == 5) {
                    button2[5].setOnAction(new EventHandler<ActionEvent>() {
            
                    @Override
                    public void handle(ActionEvent event) {
                
                        str[5] = textField[5].getText();
                        textArea.setText(str[5]);
                        
                        }
                    }); 
                    
                }
                    
            }
                
            else {
                    
                // do nothing, future code for testing amount of nodes placed
                    
                 }
                }
            }
            
        });
        
        // node creation button allows user to place a 'voltage' node
        btn.setOnAction(new EventHandler<ActionEvent>() {
            
            @Override
            public void handle(ActionEvent event) {
                
                count = 1;
                if (icount == true) {
                i+=1;
                icount = false;
                }
                canPlace = true;
            }
        });
        
        root.getChildren().add(btn);
        root.getChildren().add(textArea);
        scene.setFill(Color.GREY);
        stage.setTitle("Node Placer");
        stage.setScene(scene);
        stage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
    
}

