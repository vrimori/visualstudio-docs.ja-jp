---
title: "MSBuild でのビルド ログの取得 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild、ログ記録"
  - "ログ記録 [MSBuild]"
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 27
caps.handback.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild でのビルド ログの取得
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

を使用して、MSBuild に切り替えて、ビルド データの量を確認するかどうか、および一つ以上のファイルにビルドのデータを保存する方法を指定できます。  また、ビルド データを収集するためのカスタム ロガーを指定できます。  このトピックは対応できない MSBuild コマンド ライン スイッチについては、[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)"を参照してください。  
  
> [!NOTE]
>  Visual Studio IDE を使用してプロジェクトをビルドすると、ビルド ログを確認して、それらのビルドを修正できます。  詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](../ide/how-to-view-save-and-configure-build-log-files.md)」を参照してください。  
  
## 詳細レベルの配置  
 MSBuild を使用して詳細レベルを指定せずにプロジェクトをビルドすると、次の情報がログ出力に表示されます:  
  
-   エラー、非常に重要に分類される警告、およびメッセージ。  
  
-   ある状態イベント。  
  
-   ビルドの概要。  
  
 **\/verbosity** \(**\/v**\) スイッチを使用して、データの量が出力ログに表示されるかを制御できます。  トラブルシューティングのために、`detailed`\(`d`\) または `diagnostic` \(`diag`\) レベルのほとんどの情報を提供する詳細度を使用します。  
  
 ビルド処理は、`detailed` に **\/verbosity** 設定されていると `diagnostic`に低速に設定 **\/verbosity** 新しい場合があります。  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## ファイルへのビルド ログの保存  
 ファイルにビルドのデータを保存するには **\/fileLogger** \(**fl**\) スイッチを使用できます。  次の例では `msbuild.log`という名前のファイルにビルドのデータを保存します。  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 次の例では、ログ ファイルは `MyProjectOutput.log`という名前で、ログ出力の詳細度は `diagnostic`に設定されます。  **\/filelogparameters** \(`flp`\) スイッチを使用して、二つの設定を指定します。  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 詳細については、「[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)」を参照してください。  
  
## 複数ファイルに出力するログを保存します  
 次の例では `JustErrors.log`に `msbuild1.log`に、ログ、エラー、および `JustWarnings.log`に、警告を保存します。  例では、3 本の各ファイルのファイル番号を使用します。  ファイル番号は **\/fl** と **\/flp** スイッチの直後に指定されます \(たとえば、`/fl1` と `/flp1`\)。  
  
 ファイル 2 および 3 の **\/filelogparameters** \(`flp`\) スイッチは、を各ファイルを参照するのか、各ファイルに含まれるの内容を指定します。  ファイル名は 1 に指定されないため、`msbuild1.log` の既定の名前が使用されます。  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 詳細については、「[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)」を参照してください。  
  
## カスタム ロガーを使用する  
 <xref:Microsoft.Build.Framework.ILogger> インターフェイスを実装するマネージ型を記述することにより、独自のロガーを作成できます。  たとえば、電子メールのビルド エラーを送信する、データベースに記録したり、XML ファイルに記録するには、カスタム ロガーを使用する場合があります。  詳細については、「[ビルド ロガー](../msbuild/build-loggers.md)」を参照してください。  
  
 MSBuild コマンド ラインでは、**\/logger** スイッチを使用してカスタム ロガーを指定します。  また、既定のコンソール ロガーを無効にするには **\/noconsolelogger** スイッチを使用できます。  
  
## 参照  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [ビルド ロガー](../msbuild/build-loggers.md)   
 [マルチプロセッサ環境でのログ](../msbuild/logging-in-a-multi-processor-environment.md)   
 [転送 logger の作成](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild の概念](../msbuild/msbuild-concepts.md)