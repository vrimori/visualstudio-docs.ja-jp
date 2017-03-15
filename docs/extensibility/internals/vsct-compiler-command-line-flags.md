---
title: "VSCT コンパイラのコマンド ライン フラグ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT ファイルのコンパイル"
  - "コマンド テーブルのファイルのコンパイル (VSCT ファイル)"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VSCT コンパイラのコマンド ライン フラグ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio コマンド テーブル (VSCT) コンパイラは、.vsct ファイルのコンパイルが成功したことを確認するコマンド ライン スイッチを提供します。  
  
## <a name="command-line-parameters"></a>コマンド ライン パラメーター  
 基本的な VSCT ヘルプを表示する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **コマンド** ] ウィンドウに移動、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Tools\Bin\ フォルダーとの種類。  
  
```  
vsct /?  
```  
  
 これが返されます。  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  文字 - (ダッシュ)、/(スラッシュ) はコマンド ライン パラメーターを示すための両方の受け入れられる表記します。  
  
 許容可能なフラグとその意味は次のとおりです。  
  
|切り替え|説明|  
|------------|-----------------|  
|次元|さらに定義されたシンボルを指定します。|  
|I|追加するインクルード ファイルの参照を解決するときに使用するパスを指定します。|  
|-L|指定の <xref:System.Globalization.CultureInfo> カルチャ名、たとえば"EN-US"です。|  
|E|C# の場合、指定した項目の名前空間コマンド、[C &#124; 続けてでオブジェクトを生成します。H & #124 文字です。N]:*ファイル名*、C、C# の場合 H = C++ ヘッダー、N = = 名前空間。 名前空間は、C# の場合に必要です。|  
|-v|詳細な出力します。|  
  
 -L スイッチに対応するバイナリ .cto ファイルを生成する文字列のグループを選択するコンパイラに指示、指定された <xref:System.Globalization.CultureInfo> カルチャ名。 指定されたカルチャ名は 1 つ以上の Language 属性と一致する必要があります [文字列要素](../../extensibility/strings-element.md) .vsct ファイルにします。 親から継承されている言語の属性の文字列の要素がない場合は、 [CommandTable 要素](../../extensibility/commandtable-element.md)します。  
  
 .Vsct ファイルは、複数の文字列要素を持つことがあり、別の言語] 属性があります。 グローバリゼーションは、複数回 VSCT コンパイラを実行し、-l スイッチは、各カルチャ名の変更で実現されます。  
  
 -L スイッチで指定されたカルチャ名が文字列の任意の要素の Language 属性が一致しない場合、コンパイラは、言語と地域ではないを照合しようとします。 たとえば、"EN-US"を検出できない場合、コンパイラ試みます"en"代わりにします。 失敗すると、オペレーティング システムの現在のカルチャが試みられます。 失敗すると、それが見つかった文字列の最初の要素をコンパイルします。  
  
 コマンド テーブルで使用されるシンボルを格納する C スタイルのヘッダー ファイルを生成するか、コマンドのシンボルのオブジェクトを含む c# ファイルを生成する、-e スイッチを使用できます。  
  
 -D と – スイッチに同じ名前を持つ Cl.exe C プリプロセッサ フラグの構文があります。 – D X = y という形式の定義を XML ベースの拡張の使用 \< Defined> 内にあるテスト `Condition` 属性です。 – はインクルード パスの解決に使用 \< Include>, 、\< Extern> と \< ビットマップ> ファイル参照します。 詳細については、次を参照してください。、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)します。  
  
 VSCT コンパイラは、以前にビルドされたバイナリ ファイルを逆コンパイルもことができます。 これを行うには、指定のバイナリ ファイルの \< infile>します。   VSCT コンパイラで生成されたアセンブリ バイナリ ファイル場合、は、そのシンボルが埋め込まれた状態を持つされのシンボル名は、出力が生成されますを \< 記号> 出力のセクションです。 バイナリは、CTC コンパイラによって生成されて、出力には実際の Guid と Id が含まれます。 Ctc.exe の現在のバージョンによって生成される *.ctsym ファイルは、バイナリの入力ファイルと同じフォルダーには、シンボルがそのファイルから読み込まれの出力に使用します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)