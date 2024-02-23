# Student-Grade-Calculator-using-javaFx
import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextArea;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.HBox;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;


/**
 * JavaFX App
 */
public class App extends Application {

     public void start(Stage primaryStage) {
        primaryStage.setTitle("Grade Calculator");

        GridPane grid = new GridPane();
        grid.setAlignment(Pos.CENTER);
        grid.setHgap(10);
        grid.setVgap(10);
        grid.setPadding(new Insets(25, 25, 25, 25));

        Label[] subjectLabels = new Label[5];
        TextField[] subjectFields = new TextField[5];

        grid.add(new Label("Subject 1:"), 0, 0);
        TextField subject1Field = new TextField();
        grid.add(subject1Field, 1, 0);

        grid.add(new Label("Subject 2:"), 0, 1);
        TextField subject2Field = new TextField();
        grid.add(subject2Field, 1, 1);

        grid.add(new Label("Subject 3:"), 0, 2);
        TextField subject3Field = new TextField();
        grid.add(subject3Field, 1, 2);

        grid.add(new Label("Subject 4:"), 0, 3);
        TextField subject4Field = new TextField();
        grid.add(subject4Field, 1, 3);

        grid.add(new Label("Subject 5:"), 0, 4);
        TextField subject5Field = new TextField();
        grid.add(subject5Field, 1, 4);

        Button calculateButton = new Button("Calculate");
        HBox hbBtn = new HBox(10);
        hbBtn.setAlignment(Pos.BOTTOM_RIGHT);
        hbBtn.getChildren().add(calculateButton);
        grid.add(hbBtn, 1, 5);

        TextArea resultArea = new TextArea();
        resultArea.setEditable(false);
        grid.add(resultArea, 0, 6, 2, 1);

        calculateButton.setOnAction(event -> {
            int subject1 = Integer.parseInt(subject1Field.getText());
            int subject2 = Integer.parseInt(subject2Field.getText());
            int subject3 = Integer.parseInt(subject3Field.getText());
            int subject4 = Integer.parseInt(subject4Field.getText());
            int subject5 = Integer.parseInt(subject5Field.getText());

            int totalMarks = subject1 + subject2 + subject3 + subject4 + subject5;
            double averagePercentage = totalMarks / 5.0;

            String grade;
            if (averagePercentage >= 90) {
                grade = "A";
            } else if (averagePercentage >= 80) {
                grade = "B";
            } else if (averagePercentage >= 70) {
                grade = "C";
            } else if (averagePercentage >= 60) {
                grade = "D";
            } else {
                grade = "F";
            }

            resultArea.setText("Total Marks: " + totalMarks + "\n" +
                               "Average Percentage: " + averagePercentage + "\n" +
                               "Grade: " + grade);
        });

        Scene scene = new Scene(grid, 400, 300);
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch();
    }

}
