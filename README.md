# 30-09-lab-work
public class Main {
    public static void main(String[] args) {
        Complex a = new Complex(1, 1);
        Complex b = new Complex(0, 1);
        System.out.println(a.Arg());
        System.out.println(b);


    }
}
public class Complex {
    private double re; //Действительная часть числа
    private double im; //Мнимая часть числа

    public Complex(double re, double im) {
        this.re = re;
        this.im = im;
    }

    public Complex() // В том случае, если мы не указываем значения при создании класса
    {
        this.re = 0;
        this.im = 0;
    }


    public static Complex Sum(Complex z1, Complex z2) //Статический метод, используемый для сложения двух комплексных
    {
        return new Complex(z1.re + z2.re, z1.im + z2.im); /* Возвращаем комплексное число, чтобы хранить
                                                              его в другой переменной */
    }

    public static Complex Scalling(Complex z, Double koef) /* Опять же, статический метод для того, чтобы
                                                            умножать на скаляр. Первый парметр- объект класса Complex,
                                                            второй- скаляр, на который нужно умножить */ {
        return new Complex(koef * z.re, koef * z.im);
    }

    public static Complex Mul(Complex z1, Complex z2) {
        return new Complex(z1.re * z2.re - z1.im * z2.im, z1.re * z2.im + z2.re * z1.im); /* Сатитический метод,
                                                                                     возвращающий произведение двух чисел
                                                                                     */
    }

    public static Complex Div(Complex z1, Complex z2) // Возвращает результат деления
    {
        return new Complex((z1.re * z2.re + z1.im * z2.im) / (z2.re * z2.re + z2.im * z2.im), (z2.re * z1.im - z1.re * z2.im) / (z2.re * z2.re + z2.im * z2.im));
    }

    public Double Mod() // Метод, возвращающий модуль комплексного числа
    {
        return Math.sqrt(re * re + im * im);
    }




    @Override
    public String toString() {

        if (re != 0) {
            if(im==1)
            {
                return re+"+i";
            }
            if(im==-1)
            {
                return re+"-i";
            }
            if (im > 0) {
                return re + "+" + im + "i";
            }
            if (im < 0) {
                return re + "" + im + "i";
            }
            if (im == 0) {
                return re + "";
            }
        } else {
            if (im == 0) {
                return "0";
            } else
                if(im==1)
                    return "i";
                if(im==-1)
                return "-i";
                else
                    return im+"i";



        }
             return null;
    }

    public double Arg() {
        if (re > 0 & im > 0) {
            return Math.atan(im / re);
        }
        if (re < 0 & im >= 0) {
            return Math.PI - Math.atan(Math.abs(im / re));
        }
        if (re < 0 & im < 0) {
            return Math.PI + Math.atan(Math.abs(im / re));
        }
        if (re > 0 & im < 0) {
            return 2 * Math.PI - Math.atan(Math.abs(im / re));
        }
        if (re == 0 & im > 0) {
            return Math.PI / 2;
        }
        if (re == 0 & im < 0) {
            return 3 * Math.PI / 2;
        }
        return 0;
    }
}
