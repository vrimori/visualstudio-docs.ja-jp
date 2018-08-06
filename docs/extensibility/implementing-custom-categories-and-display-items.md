---
title: カスタム カテゴリと 表示項目を実装する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2dbb6744b925dac1bfa91a73024ef14ef9ad29ac
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499326"
---
# <a name="implement-custom-categories-and-display-items"></a>カスタム カテゴリを実装し、アイテムを表示
VSPackage は、そのテキストの色とフォントの制御を提供できます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) でカスタム カテゴリとアイテムを表示します。

 カスタム カテゴリと 表示項目が、**フォントおよび色**プロパティ ページ。 開くには、**フォントおよび色**プロパティ ページで、**ツール** メニューのをクリックして**オプション**します。 展開**環境**し**フォントおよび色**します。

 このメカニズムを使用して、Vspackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスとその関連するインターフェイス。

 原則として、このメカニズムを使用して既存のすべてを変更する**項目を表示**と**カテゴリ**を含めることができます。 ただし、この属性は変更することできません使用する必要があります、**テキスト EditorCategory**またはその**表示項目**します。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)します。

 ユーザー設定を実装する**カテゴリ**または**項目を表示**VSPackage にする必要があります。

-   作成するか、レジストリ内のカテゴリを特定します。

     IDE の実装、**フォントおよび色**プロパティ ページでは、この情報を使用して、特定のカテゴリをサポートしているサービスのクエリを正常にします。

-   作成またはレジストリに (省略可能) グループを識別します。

     2 つ以上のカテゴリの和集合を表すグループを定義することができます。 グループが定義されている場合、IDE によって自動的にサブカテゴリをマージし、配布グループ内のアイテムの表示。

-   IDE のサポートを実装します。

-   フォントと色の変更を処理します。

 詳しくは、次を参照してください。[へのアクセスには、フォントおよび色の設定が格納されている](../extensibility/accessing-stored-font-and-color-settings.md)します。

## <a name="to-create-or-identify-categories"></a>作成またはカテゴリを識別するには

-   カテゴリのレジストリ エントリの特殊な型を構築 *[hklm \software\microsoft \Visual Studio\\*\<Visual Studio のバージョン >*\FontAndColors\\ `<Category>`]*

     *\<カテゴリ >* カテゴリのローカライズされていない名前を指定します。

-   2 つの値を使用してレジストリを設定します。

    |name|型|データ|説明|
    |----------|----------|----------|-----------------|
    |カテゴリ|REG_SZ|GUID|カテゴリを識別するために作成された GUID。|
    |Package|REG_SZ|GUID|カテゴリをサポートする VSPackage のサービスの GUID です。|

 レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>の対応するカテゴリ。

## <a name="to-create-or-identify-groups"></a>グループを作成または識別するのには

-   カテゴリのレジストリ エントリの特殊な型を構築 *[hklm \software\microsoft \Visual Studio\\*\<Visual Studio のバージョン >*\FontAndColors\\* \<グループ >*]*

     *\<グループ >* はローカライズされていないグループの名前です。

-   2 つの値を使用してレジストリを設定します。

    |name|型|データ|説明|
    |----------|----------|----------|-----------------|
    |カテゴリ|REG_SZ|GUID|グループを識別する GUID が作成されます。|
    |Package|REG_SZ|GUID|カテゴリをサポートするサービスの GUID です。|

 レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>の対応するグループ。

## <a name="to-implement-ide-support"></a>IDE のサポートを実装するには

-   実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>、いずれかが返されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイスまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>インターフェイスごとに、IDE に**カテゴリ**またはグループの GUID が指定されています。

-   すべて**カテゴリ**をサポートし、VSPackage の実装の別のインスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイス。

-   メソッドの実装を通じて<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>を使用して IDE を提供する必要があります。

    -   リストの**表示項目**で、**カテゴリ。**

    -   ローカライズ可能な名前**表示項目**します。

    -   各メンバーの情報を表示**カテゴリ**します。

    > [!NOTE]
    >  すべて**カテゴリ**少なくとも 1 つ含める必要があります**表示項目**します。

-   IDE を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>いくつかのカテゴリの共用体を定義するインターフェイス。

     その実装を使用して IDE を提供します。

    -   一覧、**カテゴリ**特定のグループを構成します。

    -   インスタンスへのアクセス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>それぞれをサポートしている**カテゴリ**グループ内。

    -   ローカライズ可能なグループの名前。

-   IDE の更新。

     IDE に関する情報をキャッシュする**フォントおよびカラー**設定します。 IDE の変更後にそのため、**フォントおよびカラー**構成では、キャッシュが最新であるかどうかを確認することをお勧めします。

 キャッシュの更新を行う、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます。

## <a name="to-handle-font-and-color-changes"></a>フォントと色の変更を処理するには
 VSPackage を表示するテキストの色づけを正しくサポートする VSPackage のサポートの色づけサービスはを通じて行われたユーザーによる変更に応答する必要があります、**フォントおよび色**プロパティ ページ。 VSPackage では、、この検証を行います。

-   実装することによって IDE で生成されるイベントを処理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>インターフェイス。

     IDE は次のユーザーの変更の適切なメソッドを呼び出し、**フォントおよび色**ページ。 たとえば、呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>メソッドが新しいフォントが選択されている場合。

     - または -

-   IDE の変更をポーリングします。

     これは、システムによって実装されるを通して実行<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。 主に、永続化のサポートには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>のフォントと色の情報を取得するメソッドを使用できる**項目を表示**します。 詳細については、次を参照してください。[へのアクセスには、フォントおよび色の設定が格納されている](../extensibility/accessing-stored-font-and-color-settings.md)します。

    > [!NOTE]
    >  ポーリングによって得られた結果が正しいことに、使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得メソッドを呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [テキストの色づけのフォントと色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [アクセスには、フォントおよび色の設定が格納されています。](../extensibility/accessing-stored-font-and-color-settings.md)
- [方法: 組み込みのフォントおよび色スキームへのアクセス](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [フォントと色の概要](../extensibility/font-and-color-overview.md)