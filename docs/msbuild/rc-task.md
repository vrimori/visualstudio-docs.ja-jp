---
title: "RC Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "RC task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), RC task"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# RC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft Windows リソース コンパイラ ツール \(rc.exe\) をラップします。  **RC** タスクは、カーソル、アイコン、ビットマップ、ダイアログ ボックス、フォントなどのリソースをリソース \(.res\) ファイルにコンパイルします。  詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトの「Resource Compiler \(リソース コンパイラ\)」を参照してください。  
  
## パラメーター  
 RCタスクのパラメーターの説明を次の表に示します。  タスク パラメーターの大部分、およびいくつかのパラメーター セットは、コマンド ライン オプションに対応します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**AdditionalIncludeDirectories**|省略可能な **String\[\]** 型のパラメーターです。<br /><br /> インクルード ファイルを検索するディレクトリ一覧にディレクトリを追加します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/I** オプションの説明を参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ライン オプションのリストです。**"***\/option1 \/option2 \/option\#*" のように指定します。  他の **RC** タスク パラメーターでは表されないコマンド ライン オプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」のオプションの説明を参照してください。|  
|**Culture**|省略可能な **String** 型のパラメーターです。<br /><br /> リソースで使用されるカルチャを表すロケール ID を指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/l** オプションの説明を参照してください。|  
|**IgnoreStandardIncludePath**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、リソース コンパイラでヘッダー ファイルまたはリソース ファイルを検索するときに INCLUDE 環境変数がチェックされなくなります。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/x** オプションの説明を参照してください。|  
|**NullTerminateStrings**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、ストリング テーブル内のすべての文字列が null で終わります。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/n** オプションの説明を参照してください。|  
|**PreprocessorDefinitions**|省略可能な **String\[\]** 型のパラメーターです。<br /><br /> リソース コンパイラのプリプロセッサ シンボルを 1 つ以上定義します。  マクロ シンボルのリストを指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/d** オプションの説明を参照してください。  また、この表の **UndefinePreprocessorDefinitions** の説明も参照してください。|  
|**ResourceOutputFileName**|省略可能な **String** 型のパラメーターです。<br /><br /> リソース ファイルの名前を指定します。  リソース ファイル名を指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/fo** オプションの説明を参照してください。|  
|**ShowProgress**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、コンパイラの進行状況を示すメッセージを表示します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/v** オプションの説明を参照してください。|  
|**Source**|必須の `ITaskItem[]` 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、**\/?** コマンド ライン オプションを入力し、**\/nologo** オプションを参照してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
|**UndefinePreprocessorDefinitions**|プリプロセッサ シンボルを未定義にします。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC \(The RC Command Line\) \(RC の使用 \(RC コマンド ライン\)\)](http://go.microsoft.com/fwlink/?LinkId=155730)」の **\/u** オプションの説明を参照してください。  また、この表の **PreprocessorDefinitions** の説明も参照してください。|  
  
## 解説  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)