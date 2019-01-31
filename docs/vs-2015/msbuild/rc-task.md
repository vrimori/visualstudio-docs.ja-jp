---
title: RC タスク | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 075b3d9201cc17537d62bbe467cc8fa6d3558c35
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773102"
---
# <a name="rc-task"></a>RC タスク
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Microsoft Windows リソース コンパイラ ツールである rc.exe をラップします。 **RC** タスクは、カーソル、アイコン、ビットマップ、ダイアログ ボックス、フォントなどのリソースをコンパイルし、リソース ファイル (.res) を作成します。 詳細については、[MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Web サイトのリソース コンパイラに関するページをご覧ください。  
  
## <a name="parameters"></a>パラメーター  
 RC タスクのパラメーターの説明を次の表に示します。 タスク パラメーターの大部分とパラメーターのいくつかのセットは、コマンド ライン オプションに対応します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|省略可能な **String[]** 型のパラメーターです。<br /><br /> インクルード ファイルを検索するディレクトリのリストにディレクトリを追加します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/I** オプションを参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンドライン オプションの一覧です。**"**_/option1 /option2 /option#_" のようになります。 他の **RC** タスク パラメーターでは表されないコマンド ライン オプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の各種オプションを参照してください。|  
|**カルチャ**|省略可能な **String** 型のパラメーターです。<br /><br /> リソースで使用されているカルチャを表すロケール ID を指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/l** オプションを参照してください。|  
|**IgnoreStandardIncludePath**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、ヘッダー ファイルまたはリソース ファイルの検索時、リソース コンパイラが INCLUDE 環境変数を確認するのを防止します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/x** オプションを参照してください。|  
|**NullTerminateStrings**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、文字列テーブル内のすべての文字列が null 終端されます。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」(RC を使用する (RC コマンド ライン)) の **/n** オプションを参照してください。|  
|**PreprocessorDefinitions**|省略可能な **String[]** 型のパラメーターです。<br /><br /> リソース コンパイラに対して 1 つまたは複数のプリプロセッサ シンボルを定義します。 マクロ シンボルの一覧を指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/d** オプションを参照してください。 この表の「**UndefinePreprocessorDefinitions**」も参照してください。|  
|**ResourceOutputFileName**|省略可能な **String** 型のパラメーターです。<br /><br /> リソース ファイルの名前を指定します。 リソース ファイル名を指定します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/fo** オプションを参照してください。|  
|**ShowProgress**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、コンパイラの進捗状況について報告するメッセージが表示されます。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/v** オプションを参照してください。|  
|**ソース**|必須の `ITaskItem[]` 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、**/?** コマンドライン オプションを入力し、 **/nologo** オプションを確認してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
|**UndefinePreprocessorDefinitions**|プリプロセッサ シンボルの定義を解除します。<br /><br /> 詳細については、MSDN Web サイトの「[Using RC (The RC Command Line)](http://go.microsoft.com/fwlink/?LinkId=155730)」 (RC を使用する (RC コマンド ライン)) の **/u** オプションを参照してください。 この表の「**PreprocessorDefinitions**」も参照してください。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>「  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)
