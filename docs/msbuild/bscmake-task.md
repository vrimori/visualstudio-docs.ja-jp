---
title: "BscMake Task | Microsoft Docs"
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
  - "vc.task.bscmake"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "BscMake task (MSBuild (Visual C++))"
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# BscMake Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio IDE では、bscmake は使用されなくなりました。  Visual Studio 2008 以降、ブラウザー情報は、ソリューション フォルダーの sdf ファイルに自動的に格納されます。  
  
 Microsoft Browse Information Maintenance Utility ツール \(bscmake.exe\) をラップします。  bscmake.exe ツールは、コンパイル時に作成されるソース ブラウザー ファイル \(.sbr\) からブラウザー情報ファイル \(.bsc\) をビルドします。  .bsc ファイルを表示するには、**オブジェクト ブラウザー**を使用します。  詳細については、「[BSCMAKE リファレンス](/visual-cpp/build/reference/bscmake-reference)」を参照してください。  
  
## パラメーター  
 **BscMake**  タスクのパラメーターの説明を次の表に示します。  タスク パラメーターの大部分は、コマンド ライン オプションに対応します。  
  
|パラメーター|説明|  
|------------|--------|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ラインで指定するオプションのリストです。  たとえば、"\/*option1* \/*option2* \/*option\#*" のように指定します。  他の **BscMake** タスク パラメーターでは表されないオプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、「[BSCMAKE オプション](/visual-cpp/build/reference/bscmake-options)」でオプションの説明を参照してください。|  
|**OutputFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 既定の出力ファイル名をオーバーライドするファイル名を指定します。<br /><br /> 詳細については、「[BSCMAKE オプション](/visual-cpp/build/reference/bscmake-options)」の **\/o** オプションの説明を参照してください。|  
|**PreserveSBR**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、ノンインクリメンタル ビルドを強制的に実行します。  フル ノンインクリメンタル ビルドは .bsc ファイルが存在するかどうかに関係なく実行され、.sbr ファイルの切り詰めは行われません。<br /><br /> 詳細については、「[BSCMAKE オプション](/visual-cpp/build/reference/bscmake-options)」の **\/n** オプションの説明を参照してください。|  
|**Sources**|省略可能な **ITaskItem\[\]** 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、「[BSCMAKE オプション](/visual-cpp/build/reference/bscmake-options)」の **\/NOLOGO** オプションの説明を参照してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
  
## 解説  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)