## 2.1. Defining each component of the partial derivatives $\frac{\partial\vec{S}(u,v)}{\partial{u}}$ and $\frac{\partial\vec{S}(u,v)}{\partial{v}}$ as described in Eqs. 17 and Eq. 18, respectively:

Sxu = Derivative(Sx,u,1)<br>
Syu = Derivative(Sy,u,1)<br>
Szu = Derivative(Sz,u,1)<br>
Sxv = Derivative(Sx,v,1)<br>
Syv = Derivative(Sy,v,1)<br>
Szv = Derivative(Sz,v,1)<br>

## 2.2. Defining each component of the normal vector of surface $\vec{S}$ as shown in the numerator of the fraction in Eq. 19. Here, the cross product is calculated:

Nx(u,v) = Syu(u,v) * Szv(u,v) - Szu(u,v) * Syv(u,v)<br>
Ny(u,v) = Szu(u,v) * Sxv(u,v) - Sxu(u,v) * Szv(u,v)<br>
Nz(u,v) = Sxu(u,v) * Syv(u,v) - Syu(u,v) * Sxv(u,v)<br>

## 2.3. Defining each component $N_x(u,v)$, $N_y(u,v)$ and $N_z(u,v)$ of the unit normal vector $\vec{N}$ as described in Eq. 19:

Nxunit(u,v) = Nx(u,v)/sqrt(Nx(u,v)^2+Ny(u,v)^2+Nz(u,v)^2)<br>
Nyunit(u,v) = Ny(u,v)/sqrt(Nx(u,v)^2+Ny(u,v)^2+Nz(u,v)^2)<br>
Nzunit(u,v) = Nz(u,v)/sqrt(Nx(u,v)^2+Ny(u,v)^2+Nz(u,v)^2)<br>

## 2.4. Defining the distance $r$ between the surfaces $\vec{S}_off$ and $\vec{S}$ as shown in Eq. 20:

r = 10

## 2.5. Defining each parametric component S_xoff (u,v), S_yoff (u,v) and S_zoff (u,v) of the offset surface S ⃗_off as described in Eq. 20:

Sxoff(u,v) = Sx(u,v) + r*Nxunit(u,v)<br>
Syoff(u,v) = Sy(u,v) + r*Nyunit(u,v)<br>
Szoff(u,v) = Sz(u,v) + r*Nzunit(u,v)<br>

## 2.6. Defining the offset surface S ⃗_off:

Soff = Surface(Sxoff(u,v),Syoff(u,v),Szoff(u,v),u,0,1,v,0,1)

## 2.7. Defining each component of the partial derivatives S ⃗_uu, S ⃗_uv and S ⃗_vv, according to Eqs. 21, 22 and 23:

Sxuu = Derivative(Sx,u,2)<br>
Syuu = Derivative(Sy,u,2)<br>
Szuu = Derivative(Sz,u,2)<br>
Sxuv = Derivative(Sxu,v,1)<br>
Syuv = Derivative(Syu,v,1)<br>
Szuv = Derivative(Szu,v,1)<br>
Sxvv = Derivative(Sx,v,2)<br>
Syvv = Derivative(Sy,v,2)<br>
Szvv = Derivative(Sz,v,2)<br>

## 2.8. Defining the first fundamental form coefficients E, F and G, according to Eqs. 24, 25 and 26:

E = Sxu^2+Syu^2+Szu^2<br>
F = Sxu*Sxv+Syu*Syv+Szu*Szv<br>
G = Sxv^2+Syv^2+Szv^2<br>

## 2.9. Defining the second fundamental form coefficients H, I and J, according to Eqs. 27, 28 and 29:

H = Sxuu*Nxunit+Syuu*Nyunit+Szuu*Nzunit<br>
I = Sxuv*Nxunit+Syuv*Nyunit+Szuv*Nzunit<br>
J = Sxvv*Nxunit+Syvv*Nyunit+Szvv*Nzunit<br>

## 2.10. Defining the Gaussian curvature K and the mean curvature L, according to Eqs. 30 and 31:

K = (H*J-I^2)/(E*G-F^2)<br>
L = (E*J+G*H-2*F*I)/(2*(E*G-F^2))<br>

## 2.11. Defining the maximum principal curvature κ_max, according to Eq. 32:

k_{max} = L + sqrt(L^2-K)

## 2.12. Defining the minimum radius of normal curvature ρ, according to Eq. 33:

ρ = 1/(k_{max})

## 2.13. Creating two sliders u and v, which will be shown in Graphics Window:

u = Slider(0, 1, 0.05)<br>
v = Slider(0, 1, 0.05)<br>

## 2.14. Creating a point D on the surface S ⃗:

D = S(u,v)

## 2.15. Creating a variable which calculates ρ at point D:

radius = ρ(u,v)

## 2.16. Creating a text object which shows the value of ρ as the user changes the value of u and v on the slider control. This text object is shown in Graphics Window:

text = formulatext(radius,true,true)
