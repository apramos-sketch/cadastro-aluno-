
using Microsoft.AspNetCore.Mvc;

public class AlunoController : Controller
{
    [HttpGet]
    public IActionResult Cadastrar()
    {
        return View();
    }

    [HttpPost]
    public IActionResult Cadastrar(Aluno aluno)
    {
        if (!ModelState.IsValid)
            return View(aluno);

        return View("Confirmacao", aluno);
    }
}

using System;
using System.ComponentModel.DataAnnotations;

public class Aluno
{
    [Required]
    public string Nome { get; set; }

    [Required]
    [EmailAddress]
    public string Email { get; set; }

    [Required]
    public string RA { get; set; }

    [Required]
    public string Curso { get; set; }

    [Required]
    public DateTime DataNascimento { get; set; }
}

@model Aluno

<h1>Cadastro de Aluno</h1>

<form asp-action="Cadastrar" method="post">
    <div>
        <label asp-for="Nome"></label>
        <input asp-for="Nome" />
        <span asp-validation-for="Nome"></span>
    </div>

    <div>
        <label asp-for="Email"></label>
        <input asp-for="Email" />
        <span asp-validation-for="Email"></span>
    </div>

    <div>
        <label asp-for="RA"></label>
        <input asp-for="RA" />
        <span asp-validation-for="RA"></span>
    </div>

    <div>
        <label asp-for="Curso"></label>
        <input asp-for="Curso" />
        <span asp-validation-for="Curso"></span>
    </div>

    <div>
        <label asp-for="DataNascimento"></label>
        <input asp-for="DataNascimento" type="date" />
        <span asp-validation-for="DataNascimento"></span>
    </div>

    <button type="submit">Cadastrar</button>
</form>

@model Aluno

<h1 style="color:green;">Cadastro realizado com sucesso!</h1>

<p><strong>Nome:</strong> @Model.Nome</p>
<p><strong>Email:</strong> @Model.Email</p>
<p><strong>RA:</strong> @Model.RA</p>
<p><strong>Curso:</strong> @Model.Curso</p>
<p><strong>Data de Nascimento:</strong> @Model.DataNascimento.ToShortDateString()</p>

<a asp-action="Cadastrar">Cadastrar outro</a>
