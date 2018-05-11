---
title: アプリケーション リソースの管理 (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50825ea0d610625c69955deea1599206053fb889
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="manage-application-resources-net"></a>アプリケーション リソースの管理 (.NET)

リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。

.NET デスクトップ アプリのリソースの詳細については、「[デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)」を参照してください。

## <a name="work-with-resources"></a>リソースの処理

マネージ コード プロジェクトで、プロジェクトのプロパティ ウィンドウを開きます。 次のいずれかで、[プロパティ] ウィンドウを開くことができます。

- **ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**[プロパティ]** を選びます
- **[クイック起動]** ウィンドウで、「プロジェクト プロパティ」と入力します
- **ソリューション エクスプローラー** ウィンドウで **Alt** + **Enter** キーを押します

**[リソース]** タブをクリックします。プロジェクトにまだ *.resx* ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。

## <a name="resources-in-other-project-types"></a>他のプロジェクト タイプのリソース

.NET プロジェクトでのリソースの管理方法は、他のプロジェクト タイプと異なります。 リソースについて詳しくは、以下をご覧ください。

- ユニバーサル Windows プラットフォーム (UWP) アプリの場合は、「[アプリ リソースとリソース管理システム](/windows/uwp/app-resources/)」をご覧ください
- C++ プロジェクトの場合は、「[リソース ファイルの操作](/cpp/windows/working-with-resource-files)」および「[方法: リソースを作成する](/cpp/windows/how-to-create-a-resource)」を参照してください。

## <a name="see-also"></a>関連項目

- [デスクトップ アプリケーションのリソース (.NET Framework)](/dotnet/framework/resources/index)
