---
title: ストアドのフォントと色の設定へのアクセス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91167a2f29ae95173e9de3f4f152b2c6a295b3d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015785"
---
# <a name="access-stored-font-and-color-settings"></a>アクセスには、フォントおよび色の設定が格納されています。
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) フォントの変更された設定を格納し、レジストリの色します。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>これらの設定にアクセスするインターフェイス。

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>フォントおよび色の状態の永続化を開始するには
 次のレジストリの場所にカテゴリ別のフォントと色の情報が格納されます [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio のバージョン >* \FontAndColors\\ 。*\<CategoryGUID >*] ここで、  *\<CategoryGUID >* カテゴリの GUID です。

 そのため、永続化を開始するには、VSPackage が必要です。

-   取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>呼び出してインターフェイス`QueryService`に対してグローバル サービス プロバイダー。

     `QueryService` サービス ID の引数を使用して呼び出す必要があります`SID_SVsFontAndColorStorage`とのインターフェイス ID 引数`IID_IVsFontAndColorStorage`します。

-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>メソッドを引数として、カテゴリの GUID とモード フラグを使用して永続化するカテゴリを開きます。

     指定したモード、`fFlags`引数が値から構築された、<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>列挙体。 このモードを制御します。

    -   経由でアクセスできる設定、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。

    -   すべての設定またはユーザーを変更してを使用して取得する設定のみ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。

    -   ユーザー設定に変更を反映する方法。

    -   使用される色の値の形式です。

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>フォントおよび色の状態の永続化を使用するには
 永続化するフォントと色が含まれます。

- IDE 設定をレジストリに格納されている設定を同期しています。

- レジストリの変更情報を伝達します。

- 設定して、レジストリに格納されている設定を取得します。

  IDE 設定と記憶域の設定の同期は、きわめて透過的です。 基になる IDE が自動的に更新された設定を書き込みます**表示項目**カテゴリのレジストリ エントリにします。

  VSPackage が、イベントが生成される必要があります複数 Vspackage では、特定のカテゴリを共有している場合場合のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスを使用してストアドのレジストリ設定を変更します。

  既定では、イベントの生成は有効になっていません。 イベントの生成を有効にするを使用して、カテゴリを開く<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>します。 呼び出して、適切な IDE、カテゴリを開くと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage を実装するメソッド。

> [!NOTE]
>  によって変更、**フォントおよびカラー**プロパティ ページの独立したイベントを生成する<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>します。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスのメソッドを呼び出す前にキャッシュされているフォントおよび色の設定の更新が必要かどうかを判断、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>クラス。

### <a name="store-and-retrieve-information"></a>情報の格納および取得
 Vspackage を呼び出してユーザーを変更できるオープンのカテゴリの名前付きの表示項目の情報を構成またはを取得する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A>メソッド。

 フォントに関する情報の属性を使用して、特定のカテゴリが取得したは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A>メソッド。

> [!NOTE]
>  `fFlags`に渡される引数、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>そのカテゴリを開いたときに、メソッドの動作を定義する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>メソッド。 既定では、これらのメソッドはのみが変更されたアイテムの表示に関する情報を返します。 ただしを使用して、カテゴリが開かれている場合、<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>更新両方のフラグし、そのまま表示項目からアクセスできる<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>します。

 既定でのみ変更**表示項目**レジストリの情報が保持されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>フォントと色のすべての設定を取得するインターフェイスを使用することはできません。

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>メソッドが変更されていないについて REGDB_E_KEYMISSING、情報を取得するために使用するときに (0x80040152L) を返す**表示項目**します。

 すべての設定**表示項目**特定**カテゴリ**のメソッドを使用して取得できます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイス。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [カスタム カテゴリを実装し、アイテムを表示](../extensibility/implementing-custom-categories-and-display-items.md)