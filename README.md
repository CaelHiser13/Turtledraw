import turtle

def read_file(file_name):
    with open(file_name, 'r') as file:
        lines = [line.strip() for line in file.readlines()]
    return lines

def draw_shapes(data):
    turtle.setup(450, 450)
    turtle.speed('fastest')

    pen = turtle.Turtle()
    pen.penup()

    for line in data:
        if line == 'stop':
            pen.penup()
        else:
            values = line.split()
            color = values[0]  # Assuming color is the first value
            x, y = map(int, values[1:])  # Assuming the rest are x, y coordinates
            pen.goto(x, y)

            if color == 'black':  # Draw the turtle shape only if the color is black
                pen.pendown()
            else:
                pen.penup()

    turtle.done()

def main():
    file_name = input("Enter the name of the input file: ")
    file_data = read_file(file_name)
    draw_shapes(file_data)

if __name__ == "__main__":
    main()
 
