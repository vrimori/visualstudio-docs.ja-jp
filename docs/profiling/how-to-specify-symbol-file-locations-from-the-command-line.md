---
title: "方法: コマンド ラインからシンボル ファイルの場所を指定する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4d0e04c439f5e677cbbbdcfcf560ec976c6257b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>方法: コマンド ラインからシンボル ファイルの場所を指定する
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
  
## <a name="specifying-windows-symbol-files"></a>Windows シンボル ファイルを指定する  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows シンボル サーバーの使用を構成するには  
  
1.  必要に応じて、シンボル ファイルをローカルに格納するためのディレクトリを作成します。  
  
2.  次の構文を使用して、**_NT_SYMBOL_PATH** 環境変数または VSPerfReport /SymbolPath オプションを設定します。  
  
     **srv\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
     ここで、*LocalStore* は作成したローカル ディレクトリのパスです。  
  
## <a name="specifying-component-symbol-files"></a>コンポーネント シンボル ファイルを指定する  
 プロファイリング ツールは、プロファイルするコンポーネントの .pdb ファイルを、コンポーネントに保存されているファイルの元の場所か、プロファイル データ ファイルが含まれているフォルダー内で検索します。 **_NT_SYMBOL_PATH** または **/SymbolPath** オプションに 1 つ以上のパスを追加すれば、他の検索場所を指定できます。 セミコロンでパスを区切ります。  
  
## <a name="example"></a>例  
 次のコマンド ラインは、**_NT_SYMBOL_PATH** 環境変数を Windows シンボル サーバーに設定し、ローカル ディレクトリを **C:\Symbols** に設定します。  
  
 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 次の VSPerfReport コマンド ラインは、**/SymbolPath** オプションを使って C:\Projects\Symbols ディレクトリを検索パスに追加します。  
  
 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**