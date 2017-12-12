---
title: "アプリケーション リソースの管理 (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>アプリケーション リソースの管理 (.NET)
リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。  
  
.NET デスクトップ アプリ内でのリソースの詳細については、「 [Resources in Desktop Apps](/dotnet/framework/resources/index)」を参照してください。 C++ デスクトップ アプリ内でのリソースの詳細については、「 [Working with Resource Files](/cpp/windows/working-with-resource-files)」を参照してください。  
  
UWP アプリは、デスクトップ アプリとは異なる別のリソース モデルを使用します。 Windows 8.x アプリ内でのリソースについては、「[アプリ リソースの定義 (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx)」をご覧ください。  
  
## <a name="working-with-resources"></a>リソースの操作  
マネージ コード プロジェクトで、プロジェクトのプロパティ ウィンドウを開きます。 次のいずれかで、[プロパティ] ウィンドウを開くことができます。

- **ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**[プロパティ]** を選びます
- **[クイック起動]** ウィンドウで、「**プロジェクト プロパティ**」と入力します
- **ソリューション エクスプローラー** ウィンドウで **Alt + Enter** キーを押します

**[リソース]** タブをクリックします。プロジェクトにまだ .resx ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。  
  
リソースの作業をする方法の詳細は、「 [How to: Create a Resource](/cpp/windows/how-to-create-a-resource)」を参照してください。