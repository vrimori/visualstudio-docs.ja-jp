---
title: "方法: コマンド ラインからシンボル ファイルの場所を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法: コマンド ラインからシンボル ファイルの場所を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

関数名や行番号などのシンボル情報を表示するには、VSPerfReport コマンド ライン ツールが、プロファイリングしたコンポーネントおよび Windows システム ファイルのシンボル \(.pdf\) ファイルにアクセスできる必要があります。  シンボル ファイルは、コンポーネントのコンパイル時に作成されます。  詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  VSPerfReport は、次の場所でシンボル ファイルを自動的に検索します。  
  
-   **\/SymbolPath** オプションまたは **\_NT\_SYMBOL\_PATH** 環境変数で指定されたパス  
  
-   コンポーネントがコンパイルされた場所の正確なローカル パス  
  
-   プロファイル データ \(.vsp または .vsps\) ファイルが格納されているディレクトリ  
  
 Microsoft では、多くの製品の .pdb ファイルをオンラインのシンボル サーバーで提供しています。  レポート機能に使用しているコンピューターがインターネットに接続されている場合、VSPerfReport はオンラインのシンボル サーバーに接続してシンボル情報を自動的に検索し、そのファイルをローカル ストアに保存します。  
  
 シンボル ファイルおよび Microsoft シンボル サーバー ストアの場所は、次の方法で指定できます。  
  
-   **\_NT\_SYMBOL\_PATH** 環境変数を指定する。  
  
-   VSPerfReport コマンド ラインに **\/SymbolPath** オプションを追加する。  
  
 これらの方法の両方を使用することもできます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がローカル コンピューターにインストールされている場合は、Windows シンボル ファイルの場所が既に指定されている可能性があります。  詳細については、「[方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)」を参照してください。  このトピックで後述するように、その場所とサーバーを使用するよう VSPerfReport を構成する必要があります。  
  
## Windows シンボル ファイルの指定  
  
#### Windows シンボル サーバーの使用を構成するには  
  
1.  必要に応じて、シンボル ファイルをローカルに保存するためのディレクトリを作成します。  
  
2.  次の構文を使用して、**\_NT\_SYMBOL\_PATH** 環境変数または VSPerfReport \/SymbolPath オプションを設定します。  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     *LocalStore* が作成したローカル ディレクトリのパスです。  
  
## コンポーネントのシンボル ファイルの指定  
 プロファイリング ツールは、プロファイルするコンポーネントの .pdb ファイルを、コンポーネントに保存されているファイルの元の場所か、プロファイル データ ファイルが含まれているフォルダー内で検索します。  **\_NT\_SYMBOL\_PATH** または **\/SymbolPath** オプションに 1 つ以上のパスを追加することで、別の検索場所を指定できます。  各パスはセミコロンで区切ります。  
  
## 例  
 次のコマンド ラインは、**\_NT\_SYMBOL\_PATH** 環境変数を Windows シンボル サーバーに設定し、ローカル ディレクトリを **C:\\Symbols** に設定します。  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 次の VSPerfReport コマンド ラインは、**\/SymbolPath** オプションを使用して、検索パスに C:\\Projects\\Symbols ディレクトリを追加します。  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**