---
title: アプリケーション リソースの管理 (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ef364b5152cc822c518e02d9f0b9a4a1a4e3679
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042843"
---
# <a name="manage-application-resources-net"></a>アプリケーション リソースの管理 (.NET)

リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、「[アプリ リソースの管理 (Visual Studio for Mac)](/visualstudio/mac/managing-app-resources)」を参照してください。

.NET デスクトップ アプリのリソースの詳細については、「[デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)」を参照してください。

## <a name="work-with-resources"></a>リソースの処理

マネージド コード プロジェクトで、プロジェクトのプロパティ ウィンドウを開きます。 次のいずれかで、[プロパティ] ウィンドウを開くことができます。

- **ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**[プロパティ]** を選びます
- **[クイック起動]** ウィンドウで、「プロジェクト プロパティ」と入力します
- **ソリューション エクスプローラー**で **Alt** + **Enter** キーを押します。

**[リソース]** タブをクリックします。プロジェクトにまだ *.resx* ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。

## <a name="resources-in-other-project-types"></a>他のプロジェクト タイプのリソース

.NET プロジェクトでのリソースの管理方法は、他のプロジェクト タイプと異なります。 リソースについて詳しくは、以下をご覧ください。

- ユニバーサル Windows プラットフォーム (UWP) アプリの場合は、「[アプリ リソースとリソース管理システム](/windows/uwp/app-resources/)」をご覧ください
- C++ プロジェクトの場合は、「[リソース ファイルの操作](/cpp/windows/working-with-resource-files)」および「[方法:リソースを作成する](/cpp/windows/how-to-create-a-resource)」を参照してください

## <a name="see-also"></a>関連項目

- [デスクトップ アプリケーションのリソース (.NET Framework)](/dotnet/framework/resources/index)
- [アプリ リソースの管理 (Visual Studio for Mac)](/visualstudio/mac/managing-app-resources)
