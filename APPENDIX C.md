# APPENDIX C – DEVELOPMENT OF CUTTING PATH

## 3.1. Defining the number of splits of the surface in longitudinal and transversal directions:

ns_l = 3<br>
ns_t = 6<br>

## 3.2. Defining the amount of extension of the curve beyond the surface for each direction:

extra_l = 0.05<br>
extra_t = 0.10<br>

## 3.3. Defining the curves along the surface, based in the number of splits, slices and extension extra, for each direction, according to Eq. 34 and 35:

Curves_l = Sequence(Curve(Soff(u, v), u, 0-extra_l, 1+extra_l), v, 0, 1, 1/ns_l)<br>
Curves_t = Sequence(Curve(Soff(v, u), u, 0-extra_t, 1+extra_t), v, 0, 1, 1/ns_t)<br>

## 3.4. Defining the start and end points of each curve for transversal and longitudinal directions:

Points_l = Sequence(Sequence(Soff(u, v), u, 0-extra_l, 1+extra_l, 1+2extra_l), v, 0, 1, 1/ns_l)
Points_t = Sequence(Sequence(Soff(v, u), u, 0-extra_t,1+extra_t, 1+2extra_t), v, 0, 1, 1/ns_t)

## 3.5. Defining the connecting segments between each consecutive curve. This is also carried out for each direction:

Segments_l = Sequence(Segment(Element(Points_l, I, (-1)^I / 2 + 1.5), Element(Points_l, I + 1, (-1)^I / 2 + 1.5)), I, 1, Length(Points_l) - 1)
Segments_t = Sequence(Segment(Element(Points_t, I, (-1)^I / 2 + 1.5), Element(Points_t, I + 1, (-1)^I / 2 + 1.5)), I, 1, Length(Points_t) - 1) 

