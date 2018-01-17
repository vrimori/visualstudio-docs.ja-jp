---
title: "Visual Studio のプロジェクトと項目テンプレートに名前パラメーターを追加する | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ecdd277a36cb1c074653edb2af7f1882e6d25ede
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-substitute-parameters-in-a-template"></a>方法 : テンプレート内のパラメーターを置き換える

テンプレート パラメーターを使うと、テンプレートからファイルを作成するときに、クラス名や名前空間などの識別子を置き換えることができます。 既存のテンプレートにテンプレート パラメーターを追加することも、テンプレート パラメーターで独自のテンプレートを作成することもできます。

テンプレート パラメーターは、$*parameter*$ という形式で記述します。 テンプレート パラメーターの完全な一覧については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。

次のセクションでは、名前空間の名前を "安全なプロジェクト名" に置き換えるようにテンプレートを変更する方法を示します。

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>パラメーターを使って名前空間の名前を置き換えるには

1. テンプレートの 1 つ以上のコード ファイルにパラメーターを挿入します。 例:

    ```csharp
    namespace $safeprojectname$
    ```

1. テンプレートの .vstemplate ファイルで、このファイルを含む `ProjectItem` 要素を検索します。

1. `ProjectItem` 要素の `ReplaceParameters` 属性を `true` に設定します。

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>関連項目

[プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)  
[テンプレート パラメーター](../ide/template-parameters.md)  
[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)  
[ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)