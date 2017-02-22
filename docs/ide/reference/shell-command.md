---
title: "Shell コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - ".exe ファイル"
  - "exe ファイル"
  - "実行可能ファイル, 実行 (Visual Studio からの)"
  - "Shell コマンド"
  - "シェル, 実行 (exe ファイルの)"
  - "Tools.Shell コマンド"
  - "Visual Studio, 実行可能ファイル"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Shell コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] から実行可能プログラムを起動します。  
  
## 構文  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## 引数  
 `path`  
 必ず指定します。  実行するファイルまたは開くドキュメントのパスとファイル名。  指定したファイルが、環境変数 PATH に設定されているどのディレクトリにも入っていない場合は、完全パスを指定する必要があります。  
  
 `args`  
 省略可能です。  呼び出されるプログラムへ渡す引数。  
  
## スイッチ  
 \/commandwindow、\/command、\/c、または \/cmd  
 省略可能です。  実行可能プログラムの出力を **\[コマンド\]** ウィンドウに表示します。  
  
 \/dir:`folder` または \/d: `folder`  
 省略可能です。  プログラムの実行時に作業ディレクトリが設定されるように指定します。  
  
 \/outputwindow、\/output、\/out、または \/o  
 省略可能です。  実行可能プログラムの出力を **\[出力\]** ウィンドウに表示します。  
  
## 解説  
 \/dir、\/o、\/c の各スイッチは、`Tools.Shell` の直後に指定する必要があります。  実行可能ファイルの名前の後に指定した内容は、その実行可能ファイルへコマンド ライン引数として渡されます。  
  
 定義済みの `Shell` エイリアスは、`Tools.Shell` の代わりに使用できます。  
  
> [!CAUTION]
>  `path` 引数にディレクトリ パスとファイル名を指定する場合は、リテラルの二重引用符 \("""\) でパス名全体を囲む必要があります。次に例を示します。  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 3 個一組の二重引用符 \("""\) は、`Shell` プロセッサによって、1 個の二重引用符として解釈されます。  このため、上の例は実際には次のパス文字列を `Shell` コマンドに渡します。  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  パス文字列を連続する二重引用符 \("""\) で囲まなかった場合、Windows では、文字列のうち最初の空白までの部分が使用されます。  たとえば、上記のパス文字列を引用符で適切に囲まなかった場合、Windows では、C:\\ にある "Program" ディレクトリが検索されます。  C:\\Program.exe という実行可能ファイルが実際に存在する場合、そのファイルが違法に改ざんされたファイルであっても、目的の "c:\\Program Files\\SomeFile.exe" プログラムではなく、そのファイルが Windows によって実行されます。  
  
## 使用例  
 次のコマンドは、xcopy.exe を使用してファイル `MyText.txt` を `Text` フォルダーにコピーします。  xcopy.exe からの出力は、**\[コマンド\]** ウィンドウと **\[出力\]** ウィンドウの両方に表示されます。  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[出力\] ウィンドウ](../Topic/Output%20Window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)