---
title: VSCT コンパイラのコマンドライン フラグ |Microsoft Docs
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
ms.openlocfilehash: 0cdf74d0c6c77a2c7c22829c8aaa3e238e65703a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744888"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT コンパイラのコマンドライン フラグ
Visual Studio コマンド テーブル (VSCT) コンパイラでは、.vsct ファイルのコンパイルが成功したことを確認するコマンド ライン スイッチを提供します。  
  
## <a name="command-line-parameters"></a>コマンド ライン パラメーター  
 基本的な VSCT ヘルプを表示する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **コマンド**ウィンドウに移動、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Tools\Bin\ フォルダーとの種類。  
  
```  
vsct /?  
```  
  
 返されます。  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indicate what additional include paths to send to the preprocessor  
  -L    Specify the language to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        followed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependency checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  -(ダッシュ) 文字および/(スラッシュ) はコマンド ライン パラメーターを示すための両方の受け入れられた表記します。  
  
 許容可能なフラグとその意味は次のとおりです。  
  
|切り替え|説明|  
|------------|-----------------|  
|-D|追加定義されたシンボルを指定します。|  
|-|追加のインクルード ファイルの参照を解決するときに使用されるパスを指定します。|  
|-L|指定、<xref:System.Globalization.CultureInfo>カルチャ名、たとえば"EN-US"です。|  
|-E|出力C#コマンドの項目の指定した名前空間内のオブジェクトが続く [C&#124;H&#124;N]:*filename*場所 C = C#、H C++ ヘッダー、N = = 名前空間。 名前空間は、c# に必要です。|  
|-v|詳細な出力。|  
  
 -L スイッチに対応するバイナリ .cto ファイルを生成するために文字列のグループを選択するようにコンパイラに指示、指定された<xref:System.Globalization.CultureInfo>カルチャ名。 指定されたカルチャ名は 1 つまたは複数の Language 属性と一致する必要があります[文字列要素](../../extensibility/strings-element.md).vsct ファイルでします。 親から継承されている言語の属性の文字列要素がない場合は、 [CommandTable 要素](../../extensibility/commandtable-element.md)します。  
  
 .Vsct ファイルある複数の文字列要素は、別の言語属性があります。 グローバリゼーションは、VSCT コンパイラを複数回実行し、-l スイッチは、各カルチャ名の変更によって実現されます。  
  
 -L スイッチで指定されたカルチャ名が文字列の任意の要素の Language 属性に一致しない場合、コンパイラは、言語と地域ではない一致を試みます。 たとえば、"EN-US"が見つからない場合、コンパイラは試します"en"代わりにします。 失敗すると、オペレーティング システムの現在のカルチャが試行されます。 失敗すると、その見つけた最初の文字列要素をコンパイルします。  
  
 コマンド テーブルによって使用されているシンボルを格納する C スタイル ヘッダー ファイルを生成するコマンドのシンボルのオブジェクトを含む c# ファイルを生成するまたは-e スイッチを使用できます。  
  
 -D、- はスイッチと同じ名前を持つ Cl.exe C プリプロセッサ フラグの構文になっています。 -D X = Y という形式になっている定義を XML ベースの拡張の使用\<定義 > 内にあるテスト`Condition`属性。 -I インクルード パスを解決するために使用\<Include >、 \<Extern > と\<ビットマップ > ファイル参照。 詳細については、次を参照してください。、 [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)します。  
  
 VSCT コンパイラは、以前にビルドされたバイナリ ファイルを逆もできます。 これを行うには、指定のバイナリ ファイル、 \<infile >。   バイナリ ファイル VSCT コンパイラによって生成されますが場合、は、埋め込まれているそのシンボルがされシンボリック名に出力が生成されます、\<シンボル > の出力セクション。 バイナリは、CTC コンパイラによって生成されたが、出力には、実際の Guid と Id が含まれます。 Ctc.exe の現在のバージョンによって生成される *.ctsym ファイルは、バイナリの入力ファイルと同じフォルダーには、シンボルがそのファイルから読み込まれ、出力に使用されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)