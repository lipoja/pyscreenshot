Hierarchy
=========

.. graphviz::

    digraph G {
        rankdir=LR;
        node [fontsize=8];
        fontsize=8;

        subgraph cluster_0 {
            label = "pyscreenshot";
            style=filled;
            fillcolor=lightgrey;
            subgraph cluster_1 {
                label = "API";
                style=filled;
                fillcolor=white;

                pyscreenshot;
            }
            subgraph cluster_2 {
                style=filled;
                fillcolor=white;
                label = "plugins";

                pyscreenshot -> GtkPixbufWrapper;
                pyscreenshot -> QtGrabWindowWrapper;
                pyscreenshot -> PySideGrabWindowWrapper;
                pyscreenshot -> PilWrapper;
                pyscreenshot -> ImagemagickWrapper;
                pyscreenshot -> WxScreenWrapper;
                pyscreenshot -> ScrotWrapper;
                pyscreenshot -> MacQuartzWrapper
                pyscreenshot -> ScreencaptureWrapper
                pyscreenshot -> GnomeScreenshotWrapper
            }
        }
        subgraph cluster_3 {
            PIL;
            wxPython;
            PyQt;
            PySide;
            PyGTK;
            screencapture;
            Quartz;
            Scrot;
            Imagemagick;
            "gnome-screenshot";
        }
        subgraph cluster_4 {
            label = "GUI library";
            Qt;
            wxWidgets;
            "GTK+";
        }

        QtGrabWindowWrapper -> PyQt -> Qt;
        PySideGrabWindowWrapper -> PySide -> Qt;
        Qt -> MacOS;
        Qt -> Windows;
        Qt -> X11;

        PilWrapper -> PIL -> Windows;
        ImagemagickWrapper -> Imagemagick -> X11;
        ScrotWrapper -> Scrot -> X11;

        GnomeScreenshotWrapper -> "gnome-screenshot" -> X11;
        "gnome-screenshot" -> Wayland;

        GtkPixbufWrapper -> PyGTK -> "GTK+";
        "GTK+" -> MacOS;
        "GTK+" -> Windows;
        "GTK+" -> X11;

        WxScreenWrapper -> wxPython -> wxWidgets;
        wxWidgets -> "GTK+";
        wxWidgets -> MacOS;
        wxWidgets -> Windows;
        wxWidgets -> X11;

        MacQuartzWrapper -> Quartz -> MacOS;
        ScreencaptureWrapper -> screencapture -> MacOS;

        application -> pyscreenshot;

    }
