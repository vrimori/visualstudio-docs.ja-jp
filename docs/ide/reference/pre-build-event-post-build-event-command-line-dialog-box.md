---
title: "[ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "マクロ、ビルド イベント"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "ビルド イベント、マクロ"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [ビルド前に実行するコマンド ライン] / [ビルド後に実行するコマンド ライン] ダイアログ ボックス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

エディット ボックスに [\[ビルド イベント\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Events%20Page,%20Project%20Designer%20\(C%23\).md) のビルド前またはビルド後のイベントを直接入力したり、使用できるマクロの一覧からビルド前およびビルド後のマクロを選択したりできます。  
  
> [!NOTE]
>  ビルド前のイベントは、プロジェクトが最新の状態で、ビルドが発生しない場合には実行しません。  
  
## UI 要素の一覧  
 **コマンド ライン エディット ボックス**  
 ビルド前またはビルド後に実行するイベントを指定します。  
  
> [!NOTE]
>  .bat ファイルを実行するすべてのビルド後コマンドの前に、`call` ステートメントを追加します。  たとえば、`call C:\MyFile.bat` または `call C:\MyFile.bat call C:\MyFile2.bat` です。  
  
 **\[マクロ\]**  
 エディット ボックスを展開して、コマンド ライン エディット ボックスに挿入するマクロの一覧を表示します。  
  
 **\[マクロ テーブル\]**  
 使用可能なマクロとその値を一覧表示します。  各マクロの詳細については、以下の「マクロ」を参照してください。  コマンド ライン エディット ボックスに挿入するマクロは、一度に 1 つだけ選択できます。  
  
 **\[挿入\]**  
 マクロ テーブルで選択したマクロをコマンド ライン エディット ボックスに挿入します。  
  
### マクロ  
 次のマクロを使用すると、ファイルの位置を指定したり、複数の選択肢がある場合に入力ファイルの実際の名前を取得したりできます。  これらのマクロの大文字と小文字は区別されません。  
  
|マクロ|説明|  
|---------|--------|  
|`$(ConfigurationName)`|現在のプロジェクト構成の名前 \("Debug" など\) です。|  
|`$(OutDir)`|出力ファイルに指定されたディレクトリを示すパスです。プロジェクト ディレクトリに対する相対パスになります。  これは、Output Directory プロパティの値に解決されます。  最後に円記号 \(\\\) が含まれます。|  
|`$(DevEnvDir)`|Visual Studio のインストール ディレクトリ \(ドライブとパスで定義\) ; "" \\円記号 \(\\\) が含まれます。|  
|`$(PlatformName)`|現在対象となっているプラットフォームの名前。  たとえば、"AnyCPU" です。|  
|`$(ProjectDir)`|プロジェクトのディレクトリ \(ドライブとパスで定義\) です。最後に円記号 \(\\\) が含まれます。|  
|`$(ProjectPath)`|プロジェクトの絶対パス名 \(ドライブ、パス、基本名、およびファイル名の拡張子で定義\) です。|  
|`$(ProjectName)`|プロジェクトの基本名です。|  
|`$(ProjectFileName)`|プロジェクトのファイル名 \(基本名とファイル名の拡張子で定義\) です。|  
|`$(ProjectExt)`|プロジェクトのファイル名の拡張子です。  ファイル拡張子の前にピリオド \(.\) が挿入されます。|  
|`$(SolutionDir)`|ソリューションのディレクトリ \(ドライブとパスで定義\) です。最後に円記号 \(\\\) が含まれます。|  
|`$(SolutionPath)`|ソリューションの絶対パス名 \(ドライブ、パス、基本名、およびファイル名の拡張子で定義\) です。|  
|`$(SolutionName)`|ソリューションの基本名です。|  
|`$(SolutionFileName)`|ソリューションのファイル名 \(基本名とファイル名の拡張子で定義\) です。|  
|`$(SolutionExt)`|ソリューションのファイル名の拡張子です。  ファイル拡張子の前にピリオド \(.\) が挿入されます。|  
|`$(TargetDir)`|ビルドのプライマリ出力ファイルのディレクトリ \(ドライブとパスで定義\) です。  最後に円記号 \(\\\) が含まれます。|  
|`$(TargetPath)`|ビルドのプライマリ出力ファイルの絶対パス名 \(ドライブ、パス、基本名、およびファイル名の拡張子で定義\) です。|  
|`$(TargetName)`|ビルドのプライマリ出力ファイルの基本名です。|  
|`$(TargetFileName)`|ビルドのプライマリ出力ファイルの名前 \(基本名とファイル名の拡張子で定義\) です。|  
|`$(TargetExt)`|ビルドのプライマリ出力ファイル名の拡張子です。  ファイル拡張子の前にピリオド \(.\) が挿入されます。|  
  
## 参照  
 [Visual Studio でのカスタム ビルド イベントの指定](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [\[ビルド イベント\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Events%20Page,%20Project%20Designer%20\(C%23\).md)   
 [方法 : ビルド イベントを指定する \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [方法 : ビルド イベントを指定する \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)