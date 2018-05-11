---
title: VSCT コンパイラのコマンド ライン フラグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e2e1045adb451c7f4dd06b888fca356d26b7ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT コンパイラのコマンド ライン フラグ
Visual Studio コマンド テーブル (VSCT) コンパイラは、.vsct ファイルのコンパイルが成功したことを確認するコマンド ライン スイッチを提供します。  
  
## <a name="command-line-parameters"></a>コマンド ライン パラメーター  
 基本的な VSCT ヘルプを表示する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **コマンド**ウィンドウに移動し、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Tools\Bin\ フォルダーとの種類。  
  
```  
vsct /?  
```  
  
 これを返します。  
  
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
>  -(ダッシュ) 文字および/(スラッシュ) は両方の受け入れられた表記コマンド ライン パラメーターを示すためです。  
  
 許容可能なフラグとその意味は次のとおりです。  
  
|切り替え|説明|  
|------------|-----------------|  
|-D|追加の定義済みのシンボルを指定します。|  
|-|追加のインクルード ファイルの参照を解決するときに使用されるパスを指定します。|  
|-L|指定して、<xref:System.Globalization.CultureInfo>カルチャ名、たとえば"EN-US"です。|  
|-E|C# の場合、続いてコマンド項目の指定した名前空間内のオブジェクトを出力 [C&#124;H&#124;N]:*filename*場所 C = C# の場合、H C++ ヘッダー、N = = 名前空間。 名前空間は、C# の場合に必要です。|  
|-v|詳細出力します。|  
  
 -L スイッチに対応するバイナリ .cto ファイルを生成するために文字列のグループを選択するコンパイラに指示、指定された<xref:System.Globalization.CultureInfo>カルチャ名。 指定されたカルチャ名は 1 つ以上の言語の属性と一致する必要があります[文字列要素](../../extensibility/strings-element.md).vsct ファイルでします。 親から継承されている文字列の要素には、言語属性がなければ、 [CommandTable 要素](../../extensibility/commandtable-element.md)です。  
  
 .Vsct ファイルが複数の文字列要素を持つことがあり、さまざまな言語属性があります。 グローバリゼーションは VSCT コンパイラ複数回の実行を-l スイッチは、各カルチャ名を変更することによって実現されます。  
  
 -L スイッチによって指定されたカルチャ名に文字列の任意の要素の Language 属性が一致しない場合、コンパイラは、言語および地域ではないと一致するしようとします。 たとえば、"EN-US"を検出できない場合、コンパイラを再試行してください"en"代わりにします。 失敗すると、オペレーティング システムの現在のカルチャが試みられます。 失敗すると、それが見つかった文字列の最初の要素をコンパイルします。  
  
 コマンド テーブルによって使用されているシンボルを格納する C スタイルのヘッダー ファイルを生成するか、コマンドのシンボルのオブジェクトを含む c# ファイルを生成する、-e スイッチを使用できます。  
  
 -D および-i スイッチに同じ名前を持つ Cl.exe C プリプロセッサ フラグの構文があります。 -D X = Y という形式の定義は XML ベースの拡張するため\<定義 > 内にあるテスト`Condition`属性。 -I インクルード パスの解決に使用\<Include >、 \<Extern > と\<ビットマップ > ファイル参照。 詳細については、次を参照してください。、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)です。  
  
 VSCT コンパイラは、以前にビルドされたバイナリ ファイルをデコンパイルもできます。 これを行うには、指定のバイナリ ファイル、 \<infile >。   バイナリ ファイルは、VSCT コンパイラによって生成されて、その埋め込まれているそのシンボルとがのシンボリック名を持つ出力が生成されます、\<シンボル > 出力のセクションです。 バイナリは、CTC コンパイラによって生成されたが、出力には、実際の Guid と Id が含まれます。 Ctc.exe の現在のバージョンによって生成される *.ctsym ファイルは、バイナリの入力ファイルと同じフォルダーには、シンボルがそのファイルから読み込まれ、出力に使用されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)