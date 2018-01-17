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
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2006f565edbca8a859cd2c155645e47e083b5528
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="managing-application-resources-net"></a>アプリケーション リソースの管理 (.NET)

リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。

.NET デスクトップ アプリ内でのリソースの詳細については、「 [Resources in Desktop Apps](/dotnet/framework/resources/index)」を参照してください。

## <a name="working-with-resources"></a>リソースの処理

マネージ コード プロジェクトで、プロジェクトのプロパティ ウィンドウを開きます。 次のいずれかで、[プロパティ] ウィンドウを開くことができます。

- **ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**[プロパティ]** を選びます
- **[クイック起動]** ウィンドウで、「プロジェクト プロパティ」と入力します
- **ソリューション エクスプローラー** ウィンドウで **Alt** + **Enter** キーを押します

**[リソース]** タブをクリックします。プロジェクトにまだ .resx ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。

## <a name="resources-in-other-project-types"></a>他のプロジェクト タイプのリソース

.NET プロジェクトでのリソースの管理方法は、他のプロジェクト タイプと異なります。 リソースについて詳しくは、以下をご覧ください。

- ユニバーサル Windows プラットフォーム (UWP) アプリの場合は、「[アプリ リソースとリソース管理システム](/windows/uwp/app-resources/)」をご覧ください
- C++ プロジェクトの場合は、「[Working with Resource Files](/cpp/windows/working-with-resource-files)」(リソース ファイルの使用) および「[How to: Create a Resource](/cpp/windows/how-to-create-a-resource)」(方法: リソースを作成する) をご覧ください

## <a name="see-also"></a>関連項目

[デスクトップ アプリケーションのリソース (.NET Framework)](/dotnet/framework/resources/index)