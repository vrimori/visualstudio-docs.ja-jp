---
title: "VSIX 色コンパイラ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX 色コンパイラ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 拡張機能の色のコンパイラ ツールは、コンソール アプリケーションを既存の Visual Studio のテーマの色を表す .xml ファイルを受け取ると、.pkgdef にファイルのこれらの色は、Visual Studio で使用できるようにする変換です。 .Xml ファイルの間の違いを比較する簡単なので、このツールは、ソース管理で作成した色を管理するために便利です。 これもにフックできます。 ビルド環境、ビルドの出力は、有効な .pkgdef ファイルようにします。  
  
 **テーマの XML スキーマ**  
  
 完全なテーマの .xml ファイルになります。  
  
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
  
 \< テーマ> 要素は全体のテーマを定義します。 テーマは、少なくとも 1 つを含める必要があります \< カテゴリ> 要素。 テーマの要素は、次のように定義されます。  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|名前|[必須]テーマの名前|  
|GUID|[必須]テーマの GUID (が GUID の書式設定を一致)|  
  
 を Visual Studio のカスタム カラーを作成する場合、その色を次のテーマを定義する必要があります。 特定のテーマの色が存在していない場合、Visual Studio が明るい色のテーマからない色を読み込もうとします。  
  
|||  
|-|-|  
|**テーマの名前**|**GUID のテーマ**|  
|淡色|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|濃色|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|青|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|ハイコントラスト|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **カテゴリ**  
  
 \< カテゴリ> 要素は、テーマの色のコレクションを定義します。 カテゴリ名は、論理的なグループを示し、可能な限り狭くとして定義する必要があります。 カテゴリには、少なくとも 1 つ含める必要があります \< 色> 要素。 カテゴリ要素は、次のように定義されます。  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|名前|[必須]カテゴリの名前|  
|GUID|[必須]カテゴリの GUID (が GUID の書式設定を一致)|  
  
 **色**  
  
 \< 色> 要素は、コンポーネントまたは UI の状態の色を定義します。 カラーの優先名前付ける方式は、[UI type] [状態]。 重複するいると、「色」という単語は使用しません。 要素の型との場合、または「状態」色を適用する色が明確に表示します。 色が空でない場合があり、いずれかの一方または両方を含める必要があります、\< 背景> と \< フォア グラウンド> 要素。 色の要素は、次のように定義されます。  
  
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
  
 **バック グラウンドまたはフォア グラウンド**  
  
 \< 背景> と \< フォア グラウンド> 要素は、色の値と、UI 要素の前景色または背景の型を定義します。 これらの要素が子を持つありません。  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**属性**|**定義**|  
|型|[必須]色の種類。 次のいずれかを指定できます。<br /><br /> *CT_INVALID:* 、色は無効であるか設定します。<br /><br /> *CT_RAW:* 生 ARGB 値。<br /><br /> *CT_COLORINDEX:* 使用しないでください。<br /><br /> *CT_SYSCOLOR:* SysColor から Windows のシステム カラーです。<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX から Visual Studio の色。<br /><br /> *CT_AUTOMATIC:* 自動の色。<br /><br /> *CT_TRACK_FOREGROUND:* 使用しないでください。<br /><br /> *CT_TRACK_BACKGROUND:* 使用しないでください。|  
|ソース|[必須]16 進数で表される色の値|  
  
 __VSCOLORTYPE 列挙型でサポートされているすべての値は、Type 属性のスキーマでサポートされます。 ただし、CT_RAW と CT_SYSCOLOR のみを使用することをお勧めします。  
  
 **すべてを**  
  
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
  
 VsixColorCompiler \< XML ファイル> \< PkgDef ファイル> \< 省略可能な引数>  
  
 **引数**  
  
||||  
|-|-|-|  
|**スイッチの名前**|**ノート**|**必須またはオプション**|  
|(.Xml ファイル) の名前のないです。|最初の名前のないパラメーターは、これに変換する XML ファイルへのパスです。|必須|  
|(.Pkgdef ファイル) の名前のないです。|これは 2 番目の名前のないパラメーターは、生成された .pkgdef ファイルの出力パス。<br /><br /> 既定値: \< XML ファイル名>.pkgdef|省略可能|  
|/noLogo|印刷の製品と著作権情報を停止するこのフラグを設定します。|省略可能|  
|/?|ヘルプ情報を出力します。|省略可能|  
|/help|ヘルプ情報を出力します。|省略可能|  
  
 **例**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   VsixColorCompiler D:\xml\colors.xml/noLogo  
  
## <a name="notes"></a>ノート  
  
-   このツールでは、vc++ ランタイムの最新バージョンをインストールすることが必要です。  
  
-   1 つのファイルのみがサポートされます。 フォルダーのパスを使用して一括変換がサポートされていません。  
  
## <a name="sample-output"></a>出力例  
 このツールによって生成された .pkgdef ファイルはようになります、キーの下。  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```