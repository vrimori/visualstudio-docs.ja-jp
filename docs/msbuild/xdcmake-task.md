---
title: "XDCMake Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xdcmake"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "XDCMake task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), XDCMake task"
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XDCMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML ドキュメント ツール \(xdcmake.exe\) をラップします。このツールは、XML ドキュメント コメント \(.xdc\) ファイルを .xml ファイルにマージします。  
  
 .xdc ファイルが作成されるのは、Visual C\+\+ ソース コードでドキュメント コメントを指定し、[\/doc](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp) コンパイラ オプションを使用してコンパイルしたときです。  詳細については、「[XDCMake リファレンス](/visual-cpp/ide/xdcmake-reference)」、「[\[XML ドキュメント ジェネレーター\] プロパティ ページ](../Topic/XML%20Document%20Generator%20Tool%20Property%20Pages.md)」、および xdcmake.exe のコマンド ライン ヘルプ オプション \(**\/?**\) を参照してください。  
  
## 解説  
 既定では、xdcmake.exe ツールでサポートされるのは、一部のコマンド ライン オプションです。  追加のオプションをサポートするには、**\/old** コマンド ライン オプションを指定します。  
  
## パラメーター  
 **XDCMake** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|**AdditionalDocumentFile**|省略可能な **String\[\]** 型のパラメーターです。<br /><br /> マージする追加の .xdc ファイルを 1 つ以上指定します。<br /><br /> 詳細については、「[\[XML ドキュメント ジェネレーター\] プロパティ ページ](../Topic/XML%20Document%20Generator%20Tool%20Property%20Pages.md)」の **"追加ドキュメント ファイル"** の説明を参照してください。  また、xdcmake.exe の **\/old** コマンド ライン オプションと **\/Fs** コマンド ライン オプションも参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ラインで指定するオプションのリストです。  たとえば、"*\/option1 \/option2 \/option\#*" のように指定します。  他の **XDCMake** タスク パラメーターでは表されないオプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、「[XDCMake リファレンス](/visual-cpp/ide/xdcmake-reference)」、「[\[XML ドキュメント ジェネレーター\] プロパティ ページ](../Topic/XML%20Document%20Generator%20Tool%20Property%20Pages.md)」、および xdcmake.exe のコマンド ライン ヘルプ \(**\/?**\) を参照してください。|  
|**DocumentLibraryDependencies**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、現在のプロジェクトがソリューション内のスタティック ライブラリ \(.lib\) プロジェクトに依存しているときは、現在のプロジェクトについて、そのライブラリ プロジェクトの .xdc ファイルが .xml ファイル出力に含まれます。<br /><br /> 詳細については、「[\[XML ドキュメント ジェネレーター\] プロパティ ページ](../Topic/XML%20Document%20Generator%20Tool%20Property%20Pages.md)」の **"ドキュメント ライブラリの依存関係"** の説明を参照してください。|  
|**OutputFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 既定の出力ファイル名をオーバーライドします。  既定の名前は、処理される最初の .xdc ファイルの名前を基に生成されます。<br /><br /> 詳細については、「[XDCMake リファレンス](/visual-cpp/ide/xdcmake-reference)」の **\/out:**`filename` オプションの説明を参照してください。  また、xdcmake.exe の **\/old** コマンド ライン オプションと **\/Fo** コマンド ライン オプションも参照してください。|  
|**ProjectName**|省略可能な **String** 型のパラメーターです。<br /><br /> 現在のプロジェクトの名前です。|  
|**SlashOld**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、追加の xdcmake.exe オプションを有効にします。<br /><br /> 詳細については、xdcmake.exe の **\/old** コマンド ライン オプションを参照してください。|  
|**Sources**|必須の `ITaskItem[]` 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、「[XDCMake リファレンス](/visual-cpp/ide/xdcmake-reference)」の **\/nologo** オプションの説明を参照してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)