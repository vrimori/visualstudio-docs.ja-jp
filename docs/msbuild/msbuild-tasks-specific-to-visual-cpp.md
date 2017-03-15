---
title: "Visual C++ に固有の MSBuild タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d82c6e70e17866e4bd4d39524faafdb554508fc2
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visual C++ に固有の MSBuild タスク
タスクでは、ビルド プロセスの間に実行するコードを指定します。 Visual C++ をインストールすると、次のタスクは [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] にインストールされたタスク以外に使用できます。 詳細については、「[MSBuild (Visual C++) の概要](/visual-cpp/build/msbuild-visual-cpp-overview)」を参照してください。  
  
 タスクごとのパラメーターのほか、すべてのタスクに以下のパラメーターがあります。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`Condition`|省略可能な `String` 型のパラメーターです。<br /><br /> このタスクが実行されるかどうかを [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] エンジンが決定するために使用する `Boolean` 式です。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] でサポートされる条件の詳細については、「[MSBuild Conditions](../msbuild/msbuild-conditions.md)」(MSBuild の条件) を参照してください。|  
|`ContinueOnError`|省略可能なパラメーターです。 次の値のいずれかを含めることができます。<br /><br /> -   **WarnAndContinue** または **true**。 タスクが失敗すると、[Target](../msbuild/target-element-msbuild.md) 要素の後続のタスクとビルドの実行が継続し、タスクのすべてのエラーが警告として扱われます。<br />-   **ErrorAndContinue**。 タスクが失敗すると、`Target` 要素の後続のタスクとビルドの実行が継続し、タスクのすべてのエラーがエラーとして扱われます。<br />-   **ErrorAndStop** または **false** (既定)。 タスクが失敗すると、`Target` 要素の残りのタスクとビルドは実行されず、`Target` 要素全体とビルドは失敗したと見なされます。<br /><br /> バージョン 4.5 より前の .NET Framework では、`true` 値と `false` 値のみがサポートされます。<br /><br /> 詳細については、「[方法: タスクで発生したエラーを無視する](../msbuild/how-to-ignore-errors-in-tasks.md)」を参照してください。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[BscMake タスク](../msbuild/bscmake-task.md)|Microsoft Browse Information Maintenance Utility ツール (bscmake.exe) をラップします。|  
|[CL タスク](../msbuild/cl-task.md)|Visual C++ コンパイラ ツール (cl.exe) をラップします。|  
|[CPPClean タスク](../msbuild/cppclean-task.md)|Visual C++ プロジェクトのビルド時に MSBuild によって作成される一時ファイルを削除します。|  
|[LIB タスク](../msbuild/lib-task.md)|Microsoft 32-Bit Library Manager ツール (lib.exe) をラップします。|  
|[Link タスク](../msbuild/link-task.md)|Visual C++ リンカー ツール (link.exe) をラップします。|  
|[MIDL タスク](../msbuild/midl-task.md)|Microsoft インターフェイス定義言語 (MIDL: Microsoft Interface Definition Language) コンパイラ ツール (midl.exe) をラップします。|  
|[MT タスク](../msbuild/mt-task.md)|Microsoft マニフェスト ツール (mt.exe) をラップします。|  
|[RC タスク](../msbuild/rc-task.md)|Microsoft Windows リソース コンパイラ ツール (rc.exe) をラップします。|  
|[SetEnv タスク](../msbuild/setenv-task.md)|指定された環境変数の値を設定または削除します。|  
|[VCMessage タスク](../msbuild/vcmessage-task.md)|ビルド時の警告メッセージおよびエラー メッセージをログに記録します。|  
|[XDCMake タスク](../msbuild/xdcmake-task.md)|XML ドキュメント ツール (xdcmake.exe) をラップします。このツールは、XML ドキュメント コメント (.xdc) ファイルを .xml ファイルにマージします。|  
|[XSD タスク](../msbuild/xsd-task.md)|ソースからスキーマまたはクラス ファイルを生成する XML スキーマ定義ツール (xsd.exe) をラップします。|  
|[MSBuild リファレンス](../msbuild/msbuild-reference.md)|MSBuild システムの要素について説明します。|  
|[タスク](../msbuild/msbuild-tasks.md)|タスクについて説明します。タスクはコードの単位であり、組み合わせることでビルドを生成できます。|  
|[タスクの作成](../msbuild/task-writing.md)|タスクを作成する方法を説明します。|
