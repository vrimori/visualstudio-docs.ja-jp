---
title: '方法: 混合モードでデバッグ |Microsoft Docs'
ms.date: 11/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db26a3a68b15dcd6252f6bd02a540e105c993b54
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896059"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>方法: 混合モードでデバッグ (C#、C++、Visual Basic)

次の手順では、デバッグまとめて、混合モードとも呼ばれるマネージ コードとネイティブ コードのデバッグを有効にする方法について説明します。 2 つの混合モード デバッグ シナリオがあります。

- DLL を呼び出すアプリをネイティブ コードで記述され、DLL が管理されます。

- DLL を呼び出すアプリは、マネージ コードで記述され、DLL は、ネイティブ コードでします。 このシナリオの詳細を説明するチュートリアルについては、次を参照してください。[マネージとネイティブ コード デバッグ](../debugger/how-to-debug-managed-and-native-code.md)します。

呼び出し元のアプリ プロジェクトのマネージ コードとネイティブの両方のデバッガーを有効にすることができます**プロパティ**ページ。 設定は、ネイティブおよびマネージ アプリ間で異なります。

呼び出し元のアプリのプロジェクトへのアクセスを持っていない場合は、DLL プロジェクトから DLL をデバッグできます。 混在モード DLL のプロジェクトだけをデバッグする必要はありません。 詳細については、「[方法 :DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)」を参照してください。

> [!NOTE]
> ダイアログ ボックスやコマンド、Visual Studio の設定またはエディションによって、この記事で使用されているのとは異なる場合があります。 設定を変更するには、次のように選択します。**ツール** > **インポートおよびエクスポート設定**します。 詳細については、「[リセット設定](../ide/environment-settings.md#reset-settings)」を参照してください。

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>呼び出し元のアプリをネイティブの混合モードのデバッグを有効にします。

1. C++ プロジェクトを選択**ソリューション エクスプ ローラー**  をクリックし、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、**プロパティ**します。

1. **\<プロジェクト > プロパティ ページ**] ダイアログ ボックスで、展開**構成プロパティ**、し、[**デバッグ**します。

1. **[デバッガーの種類]** を **[混合]** または **[自動]** に設定します。

1. **[OK]** を選択します。

   ![混合モード デバッグを有効にする](../debugger/media/dbg-mixed-mode-from-native.png "混合モード デバッグを有効にします。")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>呼び出し元の管理対象アプリの混合モードのデバッグを有効にします。

1. 選択、C#または Visual Basic プロジェクトで**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。

1. 選択、**デバッグ**、タブを選び**ネイティブ コードのデバッグを有効にする**します。

1. 変更を保存するプロパティ ページを閉じます。

   ![ネイティブ コードのデバッグを有効にする](../debugger/media/dbg-mixed-mode-from-csharp.png "ネイティブ コードのデバッグを有効にします。")

> [!NOTE]
> Visual Studio 2017 のほとんどのバージョンでは、プロジェクト プロパティの代わりに *launchSettings.json* ファイルを使用して、.NET Core アプリでネイティブ コードの混合モード デバッグを有効にする必要があります。 詳細については、次を参照してください。[マネージとネイティブ コード デバッグ](../debugger/how-to-debug-managed-and-native-code.md)します。

## <a name="see-also"></a>関連項目

- [方法: DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)