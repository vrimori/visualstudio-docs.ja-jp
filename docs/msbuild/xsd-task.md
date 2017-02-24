---
title: "XSD タスク | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 13
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
ms.openlocfilehash: 9b49f1d51771700c7203f61203575e075c94ae1b

---
# <a name="xsd-task"></a>XSD タスク
ソースからスキーマまたはクラス ファイルを生成する XML スキーマ定義ツール (xsd.exe) をラップします。  
  
## <a name="parameters"></a>パラメーター  
 **XSD** タスクのパラメーターの説明を次の表に示します。  
  
-   **AdditionalOptions**  
  
     省略可能な **String** 型のパラメーターです。  
  
     コマンド ラインで指定するオプションのリストです。 たとえば、"*/option1 /option2 /option#*" のような形式です。 他の **XSD** タスク パラメーターでは表されないオプションを指定する場合は、このパラメーターを使用します。  
  
-   **GenerateFromSchema**  
  
     省略可能な **String** 型のパラメーターです。  
  
     指定したスキーマから生成される種類を指定します。  
  
     次のいずれかの値を指定します。各値は XSD オプションに対応しています。  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Language**  
  
     省略可能な **String** 型のパラメーターです。  
  
     生成されたコードに使用するプログラミング言語を指定します。  
  
     **CS** (C#、既定)、**VB** (Visual Basic)、または **JS** (JScript) のいずれかを選択します。 `System.CodeDom.Compiler.CodeDomProvider Class` を実装するクラスの完全修飾名を指定することもできます。  
  
-   **Namespace**  
  
     省略可能な **String** 型のパラメーターです。  
  
     生成する型のランタイム名前空間を指定します。  
  
-   **Sources**  
  
     必須の `ITaskItem[]` 型のパラメーターです。  
  
     タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。  
  
-   **SuppressStartupBanner**  
  
     省略可能な **Boolean** 型のパラメーターです。  
  
     `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。  
  
-   **TrackerLogDirectory**  
  
     省略可能な **String** 型のパラメーターです。  
  
     トラッカー ログのディレクトリを指定します。  
  
## <a name="see-also"></a>関連項目  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)


<!--HONumber=Feb17_HO4-->


