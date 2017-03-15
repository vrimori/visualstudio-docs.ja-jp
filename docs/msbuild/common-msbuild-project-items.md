---
title: "Common MSBuild Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, common project items"
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Common MSBuild Project Items
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] では、項目は 1 つ以上のファイルに対応する名前付きの参照です。  項目には、ファイル名、パス、バージョン番号などのメタデータが含まれます。  項目には、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のすべてのプロジェクトの種類に共通のものがあります。  これらの項目は、microsoft.build.commontypes.xsd ファイルに定義されています。  
  
## 共通の項目  
 次に、プロジェクトの共通項目の一覧を示します。  
  
### 参照  
 プロジェクト内のアセンブリ \(マネージ\) 参照を表します。  
  
|項目名|説明|  
|---------|--------|  
|HintPath|省略可能な文字列。  アセンブリの相対パスまたは絶対パスを指定します。|  
|名前|省略可能な文字列。  アセンブリの表示名を指定します \(たとえば、"System.Windows.Forms"\)。|  
|FusionName|省略可能な文字列。  項目の簡易または厳密な fusion 名を指定します。<br /><br /> この属性が存在する場合、fusion 名を得るためにアセンブリ ファイルを開く必要がないため、時間を節約できます。|  
|SpecificVersion|省略可能なブール値。  fusion 名の特定のバージョンを参照する必要があるかどうかを指定します。|  
|Aliases|省略可能な文字列。  参照の任意のエイリアスです。|  
|プライベート|省略可能なブール値。  参照を出力フォルダーにコピーする必要があるかどうかを指定します。  この属性は、Visual Studio IDE に存在する参照の **\[ローカルにコピー\]** プロパティに一致します。|  
  
### COMReference  
 プロジェクト内の COM \(アンマネージ\) コンポーネント参照を表します。  
  
|項目名|説明|  
|---------|--------|  
|名前|省略可能な文字列。  コンポーネントの表示名を指定します。|  
|Guid|省略可能な文字列。  コンポーネントの GUID を {12345678\-1234\-1234\-1234\-123456789012} の形式で指定します。|  
|VersionMajor|省略可能な文字列。  コンポーネントのメジャー バージョン番号を指定します。  たとえば、完全なバージョン番号が "5.46" である場合、"5" を指定します。|  
|VersionMinor|省略可能な文字列。  コンポーネントのマイナー バージョン番号を指定します。  たとえば、完全なバージョン番号が "5.46" である場合、"46" を指定します。|  
|LCID|省略可能な文字列。  コンポーネントの LocaleID です。|  
|WrapperTool|省略可能な文字列。  コンポーネントで使用されるラッパー ツールの名前を指定します \(たとえば、"tlbimp"\)。|  
|Isolated|省略可能なブール値。  コンポーネントが Reg\-Free コンポーネントであるかどうかを指定します。|  
  
### COMFileReference  
 ResolvedComreference ターゲットに送られるタイプ ライブラリの一覧を表します。  
  
|項目名|説明|  
|---------|--------|  
|WrapperTool|省略可能な文字列。  コンポーネントで使用されるラッパー ツールの名前を指定します \(たとえば、"tlbimp"\)。|  
  
### NativeReference  
 ネイティブ マニフェスト ファイル、またはこのようなファイルへの参照を表します。  
  
|項目名|説明|  
|---------|--------|  
|名前|必須の文字列。  マニフェスト ファイルの基本名を指定します。|  
|HintPath|必須の文字列。  マニフェスト ファイルの相対パスを指定します。|  
  
### ProjectReference  
 別のプロジェクトへの参照を表します。  
  
|項目名|説明|  
|---------|--------|  
|名前|省略可能な文字列。  参照の表示名を指定します。|  
|プロジェクト|省略可能な文字列。  参照の GUID を {12345678\-1234\-1234\-1234\-123456789012} の形式で指定します。|  
|Package|省略可能な文字列。  参照されるプロジェクト ファイルのパスを指定します。|  
  
### Compile  
 コンパイラのソース ファイルを表します。  
  
|項目名|説明|  
|---------|--------|  
|DependentUpon|省略可能な文字列。  正しくコンパイルする必要があるファイルを指定します。|  
|AutoGen|省略可能なブール値。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) で使用するプロジェクト用にファイルを生成するかどうかを指定します。|  
|Link|省略可能な文字列。  プロジェクト ファイルの影響が及ばない物理的な場所にファイルが配置されるときに表示される表記パスです。|  
|Visible|省略可能なブール値。   **の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプローラー**にファイルを表示するかどうかを指定します。|  
|CopyToOutputDirectory|省略可能な文字列。  出力ディレクトリにファイルをコピーするかどうかを判断します。  値は次のとおりです。<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### EmbeddedResource  
 生成されるアセンブリに埋め込まれるリソースを表します。  
  
|項目名|説明|  
|---------|--------|  
|DependentUpon|省略可能な文字列。  正しくコンパイルするために、このファイルが依存するファイルを指定します|  
|ジェネレーター|必須の文字列。  この項目に対して実行される任意のファイル ジェネレーターの名前です。|  
|LastGenOutput|必須の文字列。  この項目に対して実行された任意のファイル ジェネレーターによって作成されたファイルの名前です。|  
|CustomToolNamespace|必須の文字列。  名前空間を指定します。指定した名前空間で、この項目に対して実行する任意のファイル ジェネレーターによってコードが作成されます。|  
|Link|省略可能な文字列。  プロジェクトの影響が及ばない物理的な場所にファイルが配置されるときに表示される表記パスです。|  
|Visible|省略可能なブール値。   **の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプローラー**にファイルを表示するかどうかを指定します。|  
|CopyToOutputDirectory|省略可能な文字列。  出力ディレクトリにファイルをコピーするかどうかを判断します。  値は次のとおりです。<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
|LogicalName|必須の文字列。  埋め込まれるリソースの論理名です。|  
  
### Content  
 プロジェクトにコンパイルはされないものの、プロジェクトと共に埋め込まれるか発行されることのあるファイルを表します。  
  
|項目名|説明|  
|---------|--------|  
|DependentUpon|省略可能な文字列。  正しくコンパイルする必要があるファイルを指定します。|  
|ジェネレーター|必須の文字列。  この項目に対して実行する任意のファイル ジェネレーターの名前です。|  
|LastGenOutput|必須の文字列。  この項目に対して実行された任意のファイル ジェネレーターによって作成されたファイルの名前です。|  
|CustomToolNamespace|必須の文字列。  名前空間を指定します。指定した名前空間で、この項目に対して実行する任意のファイル ジェネレーターによってコードが作成されます。|  
|Link|省略可能なブール値。   **の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプローラー**にファイルを表示するかどうかを指定します。|  
|PublishState|必須の文字列。  コンテンツの発行状態を示すもので、以下のいずれかの値を取ります。<br /><br /> -   既定値<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   必須コンポーネント|  
|IsAssembly|省略可能なブール値。  ファイルがアセンブリであるかどうかを指定します。|  
|Visible|省略可能なブール値。   **の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプローラー**にファイルを表示するかどうかを指定します。|  
|CopyToOutputDirectory|省略可能な文字列。  出力ディレクトリにファイルをコピーするかどうかを判断します。  値は次のとおりです。<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### なし  
 ビルド プロセスでは使用しないことが推奨されるファイルを表します。  
  
|項目名|説明|  
|---------|--------|  
|DependentUpon|省略可能な文字列。  正しくコンパイルする必要があるファイルを指定します。|  
|ジェネレーター|必須の文字列。  この項目に対して実行される任意のファイル ジェネレーターの名前です。|  
|LastGenOutput|必須の文字列。  この項目に対して実行された任意のファイル ジェネレーターによって作成されたファイルの名前です。|  
|CustomToolNamespace|必須の文字列。  名前空間を指定します。指定した名前空間で、この項目に対して実行する任意のファイル ジェネレーターによってコードが作成されます。|  
|Link|省略可能な文字列。  プロジェクトの影響が及ばない物理的な場所にファイルが配置されるときに表示される表記パスです。|  
|Visible|省略可能なブール値。   **の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプローラー**にファイルを表示するかどうかを指定します。|  
|CopyToOutputDirectory|省略可能な文字列。  出力ディレクトリにファイルをコピーするかどうかを判断します。  値は次のとおりです。<br /><br /> 1.  Never<br />2.  Always<br />3.  PreserveNewest|  
  
### BaseApplicationManifest  
 ビルドの基本アプリケーション マニフェストを表し、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置セキュリティ情報を含みます。  
  
### CodeAnalysisImport  
 インポートする FxCop プロジェクトを表します。  
  
### インポート  
 アセンブリを表します。このアセンブリの名前空間が、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラによってインポートされます。  
  
## 参照  
 [Common MSBuild Project Properties](../msbuild/common-msbuild-project-properties.md)