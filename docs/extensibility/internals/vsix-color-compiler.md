---
title: VSIX カラー コンパイラ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144331"
---
# <a name="vsix-color-compiler"></a>VSIX カラー コンパイラ
Visual Studio 拡張機能カラー コンパイラ ツールは、コンソール アプリケーションを既存の Visual Studio のテーマの色を表す .xml ファイルを受け取ると、.pkgdef にファイルの Visual Studio でそれらの色を使用できるようにする変換です。 .Xml ファイルの間の違いを比較する簡単なので、このツールは、ソース管理でカスタムの色を管理するのに役立ちます。 これもにフックできます。 ビルド環境、ビルドの出力が有効な .pkgdef ファイルようにします。  
  
 **テーマの XML スキーマ**  
  
 次のような完全なテーマの .xml ファイルが表示。  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **テーマ**  
  
 \<テーマ > 要素は、全体のテーマを定義します。 テーマは、少なくとも 1 つを含める必要があります\<カテゴリ > 要素。 テーマの要素は、次のように定義されます。  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|名前|[必須]テーマの名前|  
|GUID|[必須]テーマの GUID (一致しなければならない GUID の書式設定)|  
  
 を Visual Studio のカスタム カラーを作成する場合、それらの色を次のテーマを定義する必要があります。 特定のテーマの色が存在しない場合、Visual Studio は明るい色のテーマからない色をロードしようとします。  
  
|||  
|-|-|  
|**テーマ名**|**テーマの GUID**|  
|淡色|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|濃色|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|青|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|ハイコントラスト|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **カテゴリ**  
  
 \<カテゴリ > 要素は、テーマの色のコレクションを定義します。 カテゴリ名は、論理的にグループ化を提供およびできるだけ狭義として定義する必要があります。 カテゴリには、少なくとも 1 つ含める必要があります\<色 > 要素。 カテゴリの要素は、次のように定義されます。  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|名前|[必須]カテゴリの名前|  
|GUID|[必須]カテゴリの GUID (一致しなければならない GUID の書式設定)|  
  
 **色**  
  
 \<色 > 要素は、コンポーネントまたは UI の状態の色を定義します。 色の推奨される名前付けスキームが [UI 型] [状態]。 重複するいると、単語"color、"を使用しないでください。 要素の型との場合、または「状態」、色を適用する、色を示す明確に必要があります。 色が空でない場合があり、いずれかまたは両方を含める必要があります、\<背景 > と\<フォア グラウンド > 要素。 色の要素は、次のように定義されます。  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|名前|[必須]色の名前|  
  
 **背景と前景**  
  
 \<背景 > と\<フォア グラウンド > 要素は、色の値と、UI 要素の前景色または背景の型を定義します。 これらの要素に子を持つありません。  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|型|[必須]色の種類。 次のいずれかを指定できます。<br /><br /> *CT_INVALID:* 色は無効であるか設定されていません。<br /><br /> *CT_RAW:* 生 ARGB 値。<br /><br /> *CT_COLORINDEX:* 使用しないでください。<br /><br /> *CT_SYSCOLOR:* SysColor から Windows のシステム カラーです。<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX から Visual Studio の色。<br /><br /> *CT_AUTOMATIC:* 自動の色。<br /><br /> *CT_TRACK_FOREGROUND:* 使用しないでください。<br /><br /> *CT_TRACK_BACKGROUND:* 使用しないでください。|  
|ソース|[必須]16 進数で表される色の値|  
  
 __VSCOLORTYPE 列挙体によってサポートされているすべての値は、型の属性のスキーマによってサポートされます。 ただし、CT_RAW と CT_SYSCOLOR のみを使用することをお勧めします。  
  
 **まとめ**  
  
 これは、有効なテーマの .xml ファイルの簡単な例です。  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>ツールを使用する方法  
 **構文**  
  
 VsixColorCompiler \<XML ファイル > \<PkgDef ファイル >\<省略可能な Args >  
  
 **引数**  
  
||||  
|-|-|-|  
|**スイッチの名前**|**ノート**|**必須またはオプション**|  
|名前のない (.xml ファイル)|最初の名前のないパラメーターで、変換を XML ファイルへのパス。|必須|  
|名前のない (.pkgdef ファイル)|2 番目の名前のないパラメーターで、生成された .pkgdef ファイルの出力パス。<br /><br /> 既定値: \<XML ファイル名 > .pkgdef|Optional|  
|/noLogo|このフラグを設定、印刷の製品および著作権情報が停止します。|Optional|  
|/?|ヘルプ情報を出力します。|Optional|  
|/help|ヘルプ情報を出力します。|Optional|  
  
 **例**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml/noLogo  
  
## <a name="notes"></a>メモ  
  
-   このツールは、vc ランタイムの最新バージョンをインストールすることが必要です。  
  
-   1 つのファイルのみサポートされます。 フォルダーのパスを使用して一括変換はサポートされていません。  
  
## <a name="sample-output"></a>出力例  
 ツールによって生成された .pkgdef ファイルはようになります、キーの下。  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```