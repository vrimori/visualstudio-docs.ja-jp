---
title: "方法: コマンド ラインからシンボル ファイルの場所を指定する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 237acc5cc58646bc9f4e1ab6d2fbe976bb7ac124
ms.contentlocale: ja-jp
ms.lasthandoff: 07/14/2017

---
# 方法: コマンド ラインからシンボル ファイルの場所を指定する
<a id="how-to-specify-symbol-file-locations-from-the-command-line" class="xliff"></a>
関数名や行番号などのシンボル情報を表示するには、VSPerfReport コマンド ライン ツールが、プロファイリングしたコンポーネントおよび Windows システム ファイルのシンボル (.pdb) ファイルにアクセスできる必要があります。 シンボル ファイルは、コンポーネントのコンパイル時に作成されます。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。 VSPerfReport は、自動的に次の場所でシンボル ファイルを検索します。  
  
-   **/SymbolPath** オプションまたは **_NT_SYMBOL_PATH** 環境変数で指定されたパス。  
  
-   コンポーネントがコンパイルされた正確なローカル パス。  
  
-   プロファイル データ (.vsp または .vsps) ファイルが格納されているディレクトリ。  
  
 Microsoft では、多くの自社製品の .pdb ファイルをオンラインのシンボル サーバーで提供しています。 レポート機能に使用しているコンピューターがインターネットに接続されている場合、VSPerfReport はオンラインのシンボル サーバーに接続してシンボル情報を自動的に検索し、そのファイルをローカル ストアに保存します。  
  
 シンボル ファイルおよび Microsoft シンボル サーバー ストアの場所は、次の方法で指定できます。  
  
-   **_NT_SYMBOL_PATH** 環境変数を設定する。  
  
-   VSPerfReport コマンド ラインに **/SymbolPath** オプションを追加する。  
  
 これらの両方の方法を使用することもできます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がローカル コンピューターにインストールされている場合は、Windows シンボル ファイルの場所が既に指定されている可能性があります。 詳細については、「[方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)」を参照してください。 このトピックで後述するように、その場所とサーバーを使用するよう VSPerfReport を構成する必要があります。  
  
## Windows シンボル ファイルを指定する
<a id="specifying-windows-symbol-files" class="xliff"></a>  
  
#### Windows シンボル サーバーの使用を構成するには
<a id="to-configure-the-use-of-the-windows-symbol-server" class="xliff"></a>  
  
1.  必要に応じて、シンボル ファイルをローカルに格納するためのディレクトリを作成します。  
  
2.  次の構文を使用して、**_NT_SYMBOL_PATH** 環境変数または VSPerfReport /SymbolPath オプションを設定します。  
  
     **srv\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     ここで、*LocalStore* は作成したローカル ディレクトリのパスです。  
  
## コンポーネント シンボル ファイルを指定する
<a id="specifying-component-symbol-files" class="xliff"></a>  
 プロファイリング ツールは、プロファイルするコンポーネントの .pdb ファイルを、コンポーネントに保存されているファイルの元の場所か、プロファイル データ ファイルが含まれているフォルダー内で検索します。 **_NT_SYMBOL_PATH** または **/SymbolPath** オプションに 1 つ以上のパスを追加すれば、他の検索場所を指定できます。 セミコロンでパスを区切ります。  
  
## 例
<a id="example" class="xliff"></a>  
 次のコマンド ラインは、**_NT_SYMBOL_PATH** 環境変数を Windows シンボル サーバーに設定し、ローカル ディレクトリを **C:\Symbols** に設定します。  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 次の VSPerfReport コマンド ラインは、**/SymbolPath** オプションを使って C:\Projects\Symbols ディレクトリを検索パスに追加します。  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
