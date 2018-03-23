---
title: ストアドのフォントおよび色の設定にアクセスする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 78fc7c343cc570742d2d246a60d3093485800132
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="accessing-stored-font-and-color-settings"></a>ストアドのフォントおよび色の設定にアクセスします。
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) がフォントを変更した設定を格納し、レジストリの色します。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>これらの設定にアクセスするインターフェイスです。

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>フォントおよび色の状態の永続化を開始するには
 次のレジストリの場所のカテゴリによってフォントと色の情報が格納されている: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version >*\FontAndColors\\ *\<CategoryGUID >*] ここで、  *\<CategoryGUID >*カテゴリの GUID です。

 そのため、永続化を開始するには、VSPackage が必要です。

-   取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスを呼び出して`QueryService`に対してグローバル サービス プロバイダー。

     `QueryService` サービス ID 引数を使用して呼び出す必要があります`SID_SVsFontAndColorStorage`とのインターフェイス ID 引数`IID_IVsFontAndColorStorage`です。

-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>を開くには、カテゴリ、カテゴリの GUID とモード フラグを引数としてを使用して永続化するメソッド。

     によって指定された、モード、`fFlags`引数が内の値から構築された、<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>列挙します。 このモードを制御します。

    -   経由でアクセスできる、設定、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスです。

    -   すべての設定またはユーザーが変更して使用して取得できる設定のみ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスです。

    -   ユーザー設定の変更を反映する方法。

    -   使用される色の値の形式です。

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>フォントおよび色の状態の永続化を使用するには
 永続化するフォントと色が含まれます。

-   レジストリに格納されている設定と、IDE 設定を同期します。

-   レジストリの変更情報を伝達します。

-   設定して、レジストリに格納されている設定を取得します。

 IDE 設定での記憶域設定を同期することはきわめて透過的です。 基になる IDE が自動的に更新された設定を書き込みます**表示項目**カテゴリのレジストリ エントリにします。

 複数の Vspackage では、特定のカテゴリを共有している場合、VSPackage がイベントが生成されることを要求する必要があるときのメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>ストアド レジストリ設定を変更するインターフェイスを使用します。

 既定では、イベントの生成は無効です。 イベントの生成を有効にするを使用してカテゴリを開く<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>です。 IDE を呼び出して、適切なカテゴリを開くと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage を実装するメソッド。

> [!NOTE]
>  によって変更を行う、**フォントおよびカラー**プロパティ ページの独立したイベントが生成され<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>です。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスのメソッドを呼び出す前にキャッシュされたフォントと色の設定の更新が必要かどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>クラスです。

### <a name="storing-and-retrieving-information"></a>格納して、情報の取得
 Vspackage を呼び出して取得については、ユーザーが開いているカテゴリの名前付きの表示項目を変更できるか、または構成する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A>メソッドです。

 フォントに関する情報の属性を使用して、特定のカテゴリを取得の<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A>メソッドです。

> [!NOTE]
>  `fFlags`に渡される引数、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>そのカテゴリが開かれたときに、メソッドの動作を定義する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>メソッドです。 既定では、これらのメソッドはのみが変更されたアイテムの表示に関する情報を返します。 ただしを使用して、カテゴリが開かれている場合、 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 、更新の両方の設定と変更の表示項目からアクセスできる<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>です。

 既定では、のみ変更**表示項目**情報は、レジストリに保持します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>フォントと色のすべての設定を取得するインターフェイスを使用することはできません。

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>メソッドは、変更に関する REGDB_E_KEYMISSING、情報の取得に使用する場合 (0x80040152L) を返す**表示項目**です。

 すべての設定**表示項目**特定の**カテゴリ**のメソッドを使用して取得できます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイスです。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [カスタム カテゴリと 表示項目を実装します。](../extensibility/implementing-custom-categories-and-display-items.md)