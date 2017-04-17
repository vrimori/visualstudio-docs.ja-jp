---
title: "XDCMake タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 491786ecc75c3a396098d434e58e4f6635a3844c
ms.lasthandoff: 04/05/2017

---
# <a name="xdcmake-task"></a>XDCMake タスク
XML ドキュメント ツール (xdcmake.exe) をラップします。このツールは、XML ドキュメント コメント (.xdc) ファイルを .xml ファイルにマージします。  
  
 Visual C++ ソース コードにドキュメンテーション コメントを記入し、[/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) コンパイラ オプションでコンパイルすると、.xdc ファイルが作成されます。 詳細については、[XDCMake リファレンス](/cpp/ide/xdcmake-reference)、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)、xdcmake.exe のコマンドライン ヘルプ オプション (**/?**) をご覧ください。  
  
## <a name="remarks"></a>コメント  
 既定では、xdcmake.exe ツールはいくつかのコマンドライン オプションをサポートしています。 **/old** コマンドライン オプションを指定すると、追加のオプションがサポートされます。  
  
## <a name="parameters"></a>パラメーター  
 **XDCMake** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|省略可能な **String[]** 型のパラメーターです。<br /><br /> 結合する追加の .xdc ファイルを 1 つまたは複数指定します。<br /><br /> 詳細については、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)の**追加のドキュメント ファイル**に関する説明をご覧ください。 xdcmake.exe については、コマンドライン オプションの **/old** と **/Fs** も参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ラインで指定するオプションのリストです。 たとえば、"*/option1 /option2 /option#*" のような形式です。 他の **XDCMake** タスク パラメーターでは表されないオプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、[XDCMake リファレンス](/cpp/ide/xdcmake-reference)、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)、xdcmake.exe のコマンドライン ヘルプ (**/?**) をご覧ください。|  
|**DocumentLibraryDependencies**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` と現在のプロジェクトがソリューションのスタティック ライブラリ (.lib) プロジェクトに依存している場合、そのライブラリ プロジェクトの .xdc ファイルが現在のプロジェクトの .xml ファイル出力に含まれます。<br /><br /> 詳細については、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)の**ドキュメント ライブラリの依存関係**に関する説明をご覧ください。|  
|**OutputFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 既定の出力ファイル名をオーバーライドします。 既定の名前は、処理される最初の .xdc ファイルの名前から派生します。<br /><br /> 詳細については、「[XDCMake リファレンス](/cpp/ide/xdcmake-reference)」の **/out:**`filename` オプションの説明を参照してください。 xdcmake.exe については、コマンドライン オプションの **/old** と **/Fo** も参照してください。|  
|**ProjectName**|省略可能な **String** 型のパラメーターです。<br /><br /> 現在のプロジェクトの名前。|  
|**SlashOld**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、追加の xdcmake.exe オプションを有効にします。<br /><br /> 詳細については、xdcmake.exe の **/old** コマンド ライン オプションを参照してください。|  
|**Sources**|必須の `ITaskItem[]` 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、「[XDCMake リファレンス](/cpp/ide/xdcmake-reference)」の **/nologo** オプションの説明を参照してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
  
## <a name="see-also"></a>関連項目  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)
