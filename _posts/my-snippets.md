[

	//Solve conflicts
    {trigger: "*", replacement: "\ast", options: "mA"},//与markdown语法冲突
    //Mine
    {trigger: "tomb", replacement: "∎", options: "t"},//墓碑符号


	//Common expressions
    {trigger: "(RHS | LHS)", replacement: "\\operatorname{[[0]]}0", options: "rmA"},

    
	//Sequence & sum formula
    {trigger: ",,(.+),", replacement: "[[0]]_1+[[0]]_2+\\cdots+[[0]]_{${0:n}}$1 ", options: "rm"},//有限和式
    {trigger: ",,(.+),([A-Za-z]),", replacement: "[[0]]_{[[1]]+1}+[[0]]_{[[1]]+2}+\\cdots+[[0]]_{${0:n}}$1", options: "rm"},//初始下标为m的有限和式
    {trigger: ",,(.+);", replacement: "[[0]]_1,[[0]]_2,\\cdots,[[0]]_{${0:n}}$1 ", options: "rm"},//有限序列
    {trigger: ",,(.+),([A-Za-z]);", replacement: "[[0]]_{[[1]]+1},[[0]]_{[[1]]+2},\\cdots,[[0]]_{${0:n}}$1", options: "rm"},//初始下标为m的有限序列
    {trigger: ",,(.+),,", replacement: "[[0]]_1+[[0]]_2+\\cdots$0 ", options: "rm"},//无限和式
    {trigger: ",,(.+),([A-Za-z]),,", replacement: "[[0]]_{[[1]]+1}+[[0]]_{[[1]]+2}+\\cdots$0", options: "rm"},//初始下标为m的无限和式
    {trigger: ",,(.+);;", replacement: "[[0]]_1,[[0]]_2,\\cdots$0 ", options: "rm"},//无限序列
    {trigger: ",,(.+),([A-Za-z]);;", replacement: "[[0]]_{[[1]]+1},[[0]]_{[[1]]+2},\\cdots$0", options: "rm"},//初始下标为m的无限序列
    
    
    //Shesh6
    {trigger: "clr", replacement: "\<font style=\"color:${0:Red}\"\>$1\<\/font\> $2", options: "tA", description: "Add colored font HTML"},
    {trigger: "\\[\\[(.*)#(.+)\\]\\]P", replacement: "[[[[0]]#[[1]]|[[1]]]]", options: "rtA", description: "Auto-prettify links (Capitalized headers)"},
    {trigger: "([^'])\\b((?![aAI])[a-zA-Z])\\b([\\n\\s\\.,])", replacement: "[[0]]$[[1]]$[[2]]", options: "rt", description: "Automatically treat lone characters as math (except a, A, I)"},
    {trigger: "\\b(-?\\d*\\.?\\d+)\\b(\\s|,|\\.\\s)", replacement: "$\\hspace{0pt}[[0]]$[[1]]", options: "rt", description: "Automatically convert numbers to math"},
    {trigger: "clr", replacement: "\\color{${0:white} $1", options: "mA", description: "Control math mode color"},
	{trigger: "\\\\mathbf{([A-Za-z])}T", replacement: "\\mathbf{[[0]]}^{\\top}", options: "rmA", description: "Transpose"},
	{trigger: "A", replacement: "\\begin{align}\n${VISUAL}\n\\end{align}", options: "mA", description: "Align visual"},


    // Delimiter
	{trigger: "avg", replacement: "\\langle $0 \\rangle $1", options: "mA"},
	{trigger: "norm", replacement: "\\lvert $0 \\rvert $1", options: "mA", priority: 1},
	{trigger: "Norm", replacement: "\\lVert $0 \\rVert $1", options: "mA", priority: 1},
	{trigger: "ceil", replacement: "\\lceil $0 \\rceil $1", options: "mA"},
	{trigger: "floor", replacement: "\\lfloor $0 \\rfloor $1", options: "mA"},
	{trigger: "mod", replacement: "|$0|$1", options: "mA"},
	{trigger: "(", replacement: "(${VISUAL})", options: "mA"},
	{trigger: "[", replacement: "[${VISUAL}]", options: "mA"},
	{trigger: "{", replacement: "{${VISUAL}}", options: "mA"},
	
	{trigger: "\\(", replacement: "($0)$1", options: "rmA", options: "rtA"},
	{trigger: "\\{", replacement: "{$0}$1", options: "rmA", options: "rtA", discription: "Auto complete {}"},
	{trigger: "\\[", replacement: "[$0]$1", options: "rmA", options: "rtA", discription: "Auto complete []"},


	{trigger: "\"", replacement: "\"$0\"$1", options: "rmA", options: "rtA", discription: "Auto complete \"\" "},
	{trigger: "lr(", replacement: "\\left( $0 \\right) $1", options: "mA"},
	{trigger: "lr{", replacement: "\\left\\{ $0 \\right\\} $1", options: "mA"},
	{trigger: "lr[", replacement: "\\left[ $0 \\right] $1", options: "mA"},
	{trigger: "lr|", replacement: "\\left| $0 \\right| $1", options: "mA"},
	{trigger: "lra", replacement: "\\left< $0 \\right> $1", options: "mA"},

	
    // Math mode
	{trigger: "mk", replacement: "${ $0 }$$1", options: "tA"},
	{trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},
	{trigger: "beg", replacement: "\\begin{$0}\n$1\n\\end{$0}", options: "mA"},
	{trigger: "cases", replacement: "\\begin{cases}\n$0\n\\end{cases}", options: "mA"},
	{trigger: "align", replacement: "\\begin{align}\n$0\n\\end{align}", options: "mA"},
	{trigger: "array", replacement: "\\begin{array}\n$0\n\\end{array}", options: "mA"},
	

    // Matrix
	{trigger: "pmat", replacement: "\\begin{pmatrix}\n$0\n\\end{pmatrix}", options: "MA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}\n$0\n\\end{bmatrix}", options: "MA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}\n$0\n\\end{Bmatrix}", options: "MA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}\n$0\n\\end{vmatrix}", options: "MA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}\n$0\n\\end{Vmatrix}", options: "MA"},
	{trigger: "matrix", replacement: "\\begin{matrix}\n$0\n\\end{matrix}", options: "MA"},

	{trigger: "pmat", replacement: "\\begin{pmatrix}$0\\end{pmatrix}", options: "nA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}$0\\end{bmatrix}", options: "nA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}$0\\end{Bmatrix}", options: "nA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}$0\\end{vmatrix}", options: "nA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}$0\\end{Vmatrix}", options: "nA"},
	{trigger: "matrix", replacement: "\\begin{matrix}$0\\end{matrix}", options: "nA"},


    // Dashes
	{trigger: "--", replacement: "–", options: "tA"},
	{trigger: "–-", replacement: "—", options: "tA"},
	{trigger: "—-", replacement: "---", options: "tA"},


    // Greek letters
	{trigger: "@a", replacement: "\\alpha", options: "mA"},
	{trigger: "@b", replacement: "\\beta", options: "mA"},
	{trigger: "@g", replacement: "\\gamma", options: "mA"},
	{trigger: "@G", replacement: "\\Gamma", options: "mA"},
	{trigger: "@d", replacement: "\\delta", options: "mA"},
	{trigger: "@D", replacement: "\\Delta", options: "mA"},
	{trigger: "@e", replacement: "\\epsilon", options: "mA"},
	{trigger: ":e", replacement: "\\varepsilon", options: "mA"},
	{trigger: "@z", replacement: "\\zeta", options: "mA"},
	{trigger: "@t", replacement: "\\theta", options: "mA"},
	{trigger: "@T", replacement: "\\Theta", options: "mA"},
	{trigger: ":t", replacement: "\\vartheta", options: "mA"},
	{trigger: "@i", replacement: "\\iota", options: "mA"},
	{trigger: "@k", replacement: "\\kappa", options: "mA"},
	{trigger: "@l", replacement: "\\lambda", options: "mA"},
	{trigger: "@L", replacement: "\\Lambda", options: "mA"},
	{trigger: "@s", replacement: "\\sigma", options: "mA"},
	{trigger: "@S", replacement: "\\Sigma", options: "mA"},
	{trigger: "@u", replacement: "\\upsilon", options: "mA"},
	{trigger: "@U", replacement: "\\Upsilon", options: "mA"},
	{trigger: "@o", replacement: "\\omega", options: "mA"},
	{trigger: "@O", replacement: "\\Omega", options: "mA"},
	{trigger: "ome", replacement: "\\omega", options: "mA"},
	{trigger: "Ome", replacement: "\\Omega", options: "mA"},


    // Text environment
    {trigger: "text", replacement: "\\text{ $0 }$1", options: "mA"},
    {trigger: "\"", replacement: "\\text{ $0 }$1", options: "mA"},

	//Modifiers
    {trigger: "sr", replacement: "^{2}", options: "mA"},
	{trigger: "cb", replacement: "^{3}", options: "mA"},
	{trigger: "rd", replacement: "^{$0}$1", options: "mA"},
	{trigger: "--", replacement: "_{$0}$1", options: "mA"},
	{trigger: "_", replacement: "_{$0}$1", options: "mA"},
    {trigger: "^", replacement: "^{$0}$1", options: "mA"},
	{trigger: "sts", replacement: "_\\text{$0}", options: "mA"},
	{trigger: "sq", replacement: "\\sqrt{ $0 }$1", options: "mA"},
	{trigger: "//", replacement: "\\frac{$0}{$1}$2", options: "mA"},
    {trigger: "invs", replacement: "^{-1}", options: "mA"},
	{trigger: "conj", replacement: "^{*}", options: "mA"},
	
	{trigger: "([a-zA-Z])hat", replacement: "\\hat{[[0]]}", options: "rmA"},
    {trigger: "(\\S+)bar", replacement: "\\bar{[[0]]}", options: "rmA", priority : 1},
	{trigger: "([a-zA-Z])dot", replacement: "\\dot{[[0]]}", options: "rmA", priority: -1},
	{trigger: "([a-zA-Z])ddot", replacement: "\\ddot{[[0]]}", options: "rmA", priority: 1},
	{trigger: "([a-zA-Z])tilde", replacement: "\\tilde{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])und", replacement: "\\underline{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])vec", replacement: "\\vec{[[0]]}", options: "rmA"},
	//{trigger: "([a-zA-Z]),\\.", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	//{trigger: "([a-zA-Z])\\.,", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	{trigger: "(${GREEK}),\\.", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA", discription: "f,. -> \boldsymbol{f}"},
	{trigger: "(${ALPHA}),\\.", replacement: "\\boldsymbol{[[0]]}", options: "rmA", discription: "f,. -> \boldsymbol{f}"},
	{trigger: "(${GREEK})\\.,", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},
	{trigger: "(${ALPHA})\\.,", replacement: "\\boldsymbol{[[0]]}", options: "rmA", discription: "f,. -> \boldsymbol{f}"},

	{trigger: "hat", replacement: "\\hat{$0}$1", options: "mA"},
    {trigger: "bar", replacement: "\\bar{$0}$1", options: "mA"},
	{trigger: "dot", replacement: "\\dot{$0}$1", options: "mA", priority: -1},
	//{trigger: "ddot", replacement: "\\ddot{$0}$1", options: "mA"},
	//{trigger: "cdot", replacement: "\\cdot", options: "mA"},
	{trigger: "tilde", replacement: "\\tilde{$0}$1", options: "mA"},
	{trigger: "und", replacement: "\\underline{$0}$1", options: "mA"},
	{trigger: "vec", replacement: "\\vec{$0}$1", options: "mA"},


	//Subscription & supscription
	{trigger: /(\\S+)\\.(\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA", description: "Auto number subscript", priority: -1},
	{trigger: "(\\S+)\\.(i|j|n|m|k|x|y|s|t){1}", replacement: "[[0]]_{[[1]]}", options: "rmA", description: "Common subscripts", priority : -1},
    {trigger: "_\\{([a-zA-Z])\\}p(\\d)", replacement: "_{[[0]]+[[1]]}", options: "rmA", description: "Common subscripts (plus)", priority : -1},
    {trigger: "_\\{([a-zA-Z])\\}m(\\d)", replacement: "_{[[0]]-[[1]]}", options: "rmA", description: "Common subscripts (minus). a.nm1 ->a_{n-1}", priority : -1},

	// More auto letter subscript
    //{trigger: /([A-Za-z])_(\d\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA"},
	//{trigger: /\\hat{([A-Za-z])}(\d)/, replacement: "\\hat{[[0]]}_{[[1]]}", options: "rmA"},
	//{trigger: /\\vec{([A-Za-z])}(\d)/, replacement: "\\vec{[[0]]}_{[[1]]}", options: "rmA"},
	//{trigger: /\\mathbf{([A-Za-z])}(\d)/, replacement: "\\mathbf{[[0]]}_{[[1]]}", options: "rmA"},

    //{trigger: "xnn", replacement: "x_{n}", options: "mA"},
	//{trigger: "\\xii", replacement: "x_{i}", options: "mA", priority: 1},
	//{trigger: "xjj", replacement: "x_{j}", options: "mA"},
	//{trigger: "xp1", replacement: "x_{n+1}", options: "mA"},
	//{trigger: "ynn", replacement: "y_{n}", options: "mA"},
	//{trigger: "yii", replacement: "y_{i}", options: "mA"},
	//{trigger: "yjj", replacement: "y_{j}", options: "mA"},


	//Common symbols
    {trigger: /([^\\])(exp|log|ln)/, replacement: "[[0]]\\[[1]]", options: "rmA", discription: "exp, log and ln operators"},
	{trigger: "ee", replacement: "\\mathrm{e}^{ $0 }$1", options: "mA"},
    {trigger: "Re", replacement: "\\mathrm{Re}", options: "mA"},
	{trigger: "Im", replacement: "\\mathrm{Im}", options: "mA"},
    {trigger: "bf", replacement: "\\mathbf{$0}", options: "mA"},
	{trigger: "rm", replacement: "\\mathrm{$0}$1", options: "mA"},
    {trigger: "Cov", replacement: "\\mathrm{Cov}$0", options: "mA"},
    {trigger: "Var", replacement: "\\mathrm{Var}$0", options: "mA"},
    {trigger: "inf", replacement: "\\inf", options: "mA"},
    {trigger: "sup", replacement: "\\sup", options: "mA"},

	
	// Linear algebra
    {trigger: /([^\\])(det)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "trace", replacement: "\\mathrm{Tr}", options: "mA"},
    

    // Symbols
    {trigger: "ooo", replacement: "\\infty", options: "mA"},
	{trigger: "sum", replacement: "\\sum", options: "mA"},
	{trigger: "prod", replacement: "\\prod", options: "mA"},
	//{trigger: "\\sum", replacement: "\\sum_{${0:i}=${1:1}}^{${2:N}} $3", options: "m"},
	{trigger: "nsum", replacement: "\\sum_{${0:i}=${1:1}}^{${2:n}}$3", options: "mA", description: "Articulated sum"},
    {trigger: "nprod", replacement: "\\prod_{${0:i}=${1:1}}^{${2:n}} $3", options: "mA"},
    
    {trigger: "lim", replacement: "\\lim_{ ${0:n} \\to ${1:\\infty} } $2", options: "mA"},
    {trigger: "+-", replacement: "\\pm", options: "mA"},
	{trigger: "-+", replacement: "\\mp", options: "mA"},
    {trigger: "...", replacement: "\\dots", options: "mA"},
    {trigger: "v...", replacement: "\\vdots", options: "mA"},
    {trigger: "c...", replacement: "\\vdots", options: "mA"},
    {trigger: "nabl", replacement: "\\nabla", options: "mA"},
	{trigger: "del", replacement: "\\nabla", options: "mA"},
    {trigger: "xx", replacement: "\\times", options: "mA"},
    //{trigger: "**", replacement: "\\cdot", options: "mA"},
    {trigger: "para", replacement: "\\parallel", options: "mA"},

	{trigger: "===", replacement: "\\equiv", options: "mA"},
    {trigger: "!=", replacement: "\\neq", options: "mA"},
	{trigger: ">=", replacement: "\\geq", options: "mA"},
	{trigger: "<=", replacement: "\\leq", options: "mA"},
	{trigger: ">>", replacement: "\\gg", options: "mA"},
	{trigger: "<<", replacement: "\\ll", options: "mA"},
	{trigger: "simm", replacement: "\\sim", options: "mA"},
	{trigger: "sim=", replacement: "\\simeq", options: "mA"},
    {trigger: "prop", replacement: "\\propto", options: "mA"},


	//Arrows
    {trigger: "<->", replacement: "\\leftrightarrow ", options: "mA"},
	{trigger: "->", replacement: "\\to", options: "mA"},
	{trigger: "to", replacement: "\\to", options: "m"},
	{trigger: "!>", replacement: "\\mapsto", options: "mA"},
    {trigger: "=>", replacement: "\\implies", options: "mA"},
    {trigger: "=>", replacement: "$\\implies$", options: "rA"},
	{trigger: "=<", replacement: "\\impliedby", options: "mA"},
    {trigger: "t=", replacement: "\\triangleq$0", options: "mA"},
    {trigger: "x->", replacement: "\\xrightarrow{$0}", options: "mA"},
    {trigger: "uparrow", replacement: "\\uparrow ", options: "mA"},

	//Set symbols
	{trigger: "and", replacement: "\\cap", options: "mA", priority: -1},
	{trigger: "orr", replacement: "\\cup", options: "mA", priority: -1},
    {trigger: "in", replacement: "\\in ", options: "mA", priority: -1},
	//{trigger: "inn", replacement: "\\in", options: "mA"},
	{trigger: "notin", replacement: "\\not\\in", options: "mA"},
    {trigger: "\\\\\\", replacement: "\\setminus", options: "mA"},
    {trigger: "sub=", replacement: "\\subseteq", options: "mA"},
    {trigger: "sup=", replacement: "\\supseteq", options: "mA"},
	{trigger: "eset", replacement: "\\emptyset", options: "mA"},
	{trigger: "set", replacement: "\\{ $0 \\}$1", options: "mA"},
	{trigger: "e\\xists", replacement: "\\exists", options: "mA", priority: 1},
	{trigger: "exists", replacement: "$\\exists$", options: "t", priority: 1},
	{trigger: "aand", replacement: "\\wedge", options: "mA"},
	{trigger: "oorr", replacement: "\\vee", options: "mA"},
	
	{trigger: "bcap([A-Za-z])", replacement: "\\bigcap_{$0:[[0]]}$1", options: "rmA"},//交集符号
	{trigger: "bcup([A-Za-z])", replacement: "\\bigcup_{$0:[[0]]}$1", options: "rmA"},//并集符号

	
	//Font environment & Fonted letters
	{trigger: "LL", replacement: "\\mathcal{L}", options: "mA"},
	{trigger: "HH", replacement: "\\mathcal{H}", options: "mA"},
	{trigger: "CC", replacement: "\\mathbb{C}", options: "mA"},
	{trigger: "RR", replacement: "\\mathbb{R}", options: "mA"},
	{trigger: "ZZ", replacement: "\\mathbb{Z}", options: "mA"},
	{trigger: "NN", replacement: "\\mathbb{N}", options: "mA"},
    {trigger: "LL", replacement: "\\mathcal{L}", options: "mA"},
    {trigger: "HH", replacement: "\\mathcal{H}", options: "mA"},
    {trigger: "CC", replacement: "\\mathbb{C}", options: "mA"},
    {trigger: "ZZ", replacement: "\\mathbb{Z}", options: "mA"},
    {trigger: "EE", replacement: "\\mathbb{E}", options: "mA"},
    {trigger: "PP", replacement: "\\mathbb{P}", options: "mA"},
    
    {trigger: "ell", replacement: "\\ell", options: "mA"},
    {trigger: "lll", replacement: "\\ell", options: "mA"},
    
    {trigger: "\\d", replacement: "\\mathrm{d}", options: "mA"},
    {trigger: "cal", replacement: "\\mathcal{$0}$1", options: "mA"},
    {trigger: "bb", replacement: "\\mathbb{$0}$1", options: "m"},
    {trigger: "scr", replacement: "\\mathscr{$0}$1", options: "mA"},


    // Handle spaces and backslashes
    // Snippet variables can be used as shortcuts when writing snippets.
    // For example, ${GREEK} below is shorthand for "alpha|beta|gamma|Gamma|delta|..."
    // You can edit snippet variables under the Advanced snippet settings section.
	{trigger: "([^\\\\])(${GREEK})", replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before Greek letters"},
	{trigger: "([^\\\\])(${SYMBOL})", replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before symbols"},


    // Insert space after Greek letters and symbols
	// {trigger: "\\\\(${GREEK}|${SYMBOL}|${MORE_SYMBOLS})([A-Za-z])", replacement: "\\[[0]] [[1]]", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) sr", replacement: "\\[[0]]^{2}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) cb", replacement: "\\[[0]]^{3}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) rd", replacement: "\\[[0]]^{$0}$1", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) hat", replacement: "\\hat{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) dot", replacement: "\\dot{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) bar", replacement: "\\bar{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) vec", replacement: "\\vec{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) tilde", replacement: "\\tilde{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) und", replacement: "\\underline{\\[[0]]}", options: "rmA"},


    // Derivatives and integrals
    {trigger: "par", replacement: "\\frac{ \\partial ${0:y} }{ \\partial ${1:x} } $2", options: "m"},
    {trigger: /pa([A-Za-z])([A-Za-z])/, replacement: "\\frac{ \\partial [[0]] }{ \\partial [[1]] } ", options: "rm"},
    {trigger: "ddt", replacement: "\\frac{d}{dt} ", options: "mA"},

    {trigger: /([^\\])int/, replacement: "[[0]]\\int", options: "mA", priority: -1},
    {trigger: "\\int", replacement: "\\int $0 \\, d${1:x} $2", options: "m"},
    {trigger: "dint", replacement: "\\int_{${0:0}}^{${1:1}} $2 \\, d${3:x} $4", options: "mA"},
    {trigger: "oint", replacement: "\\oint", options: "mA"},
	{trigger: "iint", replacement: "\\iint", options: "mA"},
    {trigger: "iiint", replacement: "\\iiint", options: "mA"},
    {trigger: "oinf", replacement: "\\int_{0}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},
	{trigger: "infi", replacement: "\\int_{-\\infty}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},


    // Trigonometry
    {trigger: /([^\\])(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)/, replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before trig funcs"},

    {trigger: /\\(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)([A-Za-gi-z])/,
     replacement: "\\[[0]] [[1]]", options: "rmA",
     description: "Add space after trig funcs. Skips letter h to allow sinh, cosh, etc."},

    {trigger: /\\(sinh|cosh|tanh|coth)([A-Za-z])/,
     replacement: "\\[[0]] [[1]]", options: "rmA",
     description: "Add space after hyperbolic trig funcs"},


    // Visual operations
	{trigger: "U", replacement: "\\underbrace{ ${VISUAL} }_{ $0 }", options: "mA"},
	{trigger: "O", replacement: "\\overbrace{ ${VISUAL} }^{ $0 }", options: "mA"},
	{trigger: "B", replacement: "\\underset{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "C", replacement: "\\cancel{ ${VISUAL} }", options: "mA"},
	{trigger: "K", replacement: "\\cancelto{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "S", replacement: "\\sqrt{ ${VISUAL} }", options: "mA"},
	{trigger: "b", replacement: "\\mathbb{ ${VISUAL} }", options: "mA"},

	
    // Text
    
    // Automatically convert standalone letters in text to math (except a, A, I).
    // (Un-comment to enable)
    //{trigger: /([^'])\b([B-HJ-Zb-z])\b([\n\s.,?!:'])/, replacement: "[[0]]$[[1]]$[[2]]", options: "tA"},
    {trigger: / \b([B-HJ-Zb-z])\b /, replacement: " $[[0]]$ ", options: "tA"},
    {trigger: /([^'])\b(${GREEK})\b([\n\s.,?!:'])/, replacement: "[[0]]$\\[[1]]$[[2]]", options: "tA"},

    // Automatically convert Greek letters in text to math.
    // {trigger: "(${GREEK})([\\n\\s.,?!:'])", replacement: "$\\[[0]]$[[1]]", options: "rtAw"},

    // Automatically convert text of the form "x=2" and "x=n+1" to math.
    // {trigger: /([A-Za-z]=\d+)([\n\s.,?!:'])/, replacement: "$[[0]]$[[1]]", options: "rtAw"},
    // {trigger: /([A-Za-z]=[A-Za-z][+-]\d+)([\n\s.,?!:'])/, replacement: "$[[0]]$[[1]]", options: "tAw"},

    // Physics
	//{trigger: "kbt", replacement: "k_{B}T", options: "mA"},
	//{trigger: "msun", replacement: "M_{\\odot}", options: "mA"},


    // Quantum mechanics
    //{trigger: "dag", replacement: "^{\\dagger}", options: "mA"},
	//{trigger: "o+", replacement: "\\oplus ", options: "mA"},
	//{trigger: "ox", replacement: "\\otimes ", options: "mA"},
    //{trigger: "bra", replacement: "\\bra{$0} $1", options: "mA"},
	//{trigger: "ket", replacement: "\\ket{$0} $1", options: "mA"},
	//{trigger: "brk", replacement: "\\braket{ $0 | $1 } $2", options: "mA"},
    //{trigger: "outer", replacement: "\\ket{${0:\\psi}} \\bra{${0:\\psi}} $1", options: "mA"},


    // Chemistry
	//{trigger: "pu", replacement: "\\pu{ $0 }", options: "mA"},
	//{trigger: "cee", replacement: "\\ce{ $0 }", options: "mA"},
	//{trigger: "he4", replacement: "{}^{4}_{2}He ", options: "mA"},
	//{trigger: "he3", replacement: "{}^{3}_{2}He ", options: "mA"},
	//{trigger: "iso", replacement: "{}^{${0:4}}_{${1:2}}${2:He}", options: "mA"},


    // Snippet replacements can have placeholders.
    
	{trigger: "tayl", replacement: "${0:f}(${1:x} + ${2:h}) = ${0:f}(${1:x}) + ${0:f}'(${1:x})${2:h} + ${0:f}''(${1:x}) \\frac{${2:h}^{2}}{2!} + \\dots$3", options: "mA", description: "Taylor expansion"},


    // Snippet replacements can also be JavaScript functions.
    // See the documentation for more information.
	{trigger: /iden(\d)/, replacement: (match) => {
		const n = match[1];

		let arr = [];
		for (let j = 0; j < n; j++) {
			arr[j] = [];
			for (let i = 0; i < n; i++) {
				arr[j][i] = (i === j) ? 1 : 0;
			}
		}

		let output = arr.map(el => el.join(" & ")).join(" \\\\\n");
		output = `\\begin{pmatrix}\n${output}\n\\end{pmatrix}`;
		return output;
	}, options: "mA", description: "N x N identity matrix"},
]