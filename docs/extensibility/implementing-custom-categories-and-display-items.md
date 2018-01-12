---
title: "カスタム カテゴリと 表示項目を実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2dedd54aa1db26e38b6f212c616bd38c09018961
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-custom-categories-and-display-items"></a>カスタム カテゴリと 表示項目を実装します。
VSPackage が提供できるフォントのコントロールおよびそのテキストの色、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) でカスタムのカテゴリとアイテムを表示します。  
  
 カスタム カテゴリとアイテムを表示、**フォントおよび色**プロパティ ページ。 開くには、**フォントおよび色**プロパティ ページで、**ツール** メニューのをクリックして**オプション**です。 展開**環境** をクリックし、**フォントおよび色**です。  
  
 Vspackage を実装する必要がありますこのメカニズムを使用する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスとその関連するインターフェイスです。  
  
 原則として、このメカニズムを使用して既存のすべてを変更する**項目を表示**と**カテゴリ**が含まれていること。 ただし、その指定しないでを変更する、**テキスト EditorCategory**またはその**項目を表示**です。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)です。  
  
 ユーザー設定を実装する**カテゴリ**または**項目を表示**VSPackage にする必要があります。  
  
-   作成または、レジストリ内のカテゴリを指定します。  
  
     IDE の実装、**フォントおよび色**プロパティ ページでは、この情報を使用して、正しく指定されたカテゴリをサポートするサービスを照会します。  
  
-   作成するか、レジストリ内のグループ (省略可能) を特定します。  
  
     2 つまたは複数のカテゴリの和集合を表すグループを定義すると便利ですがある可能性があります。 グループが定義されている場合、IDE は自動的にサブカテゴリをマージし、配布グループ内のアイテムを表示します。  
  
-   IDE のサポートを実装します。  
  
-   フォントと色の変更を処理します。  
  
 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)です。  
  
## <a name="to-create-or-identify-categories"></a>作成またはカテゴリを識別するには  
  
-   カテゴリのレジストリ エントリの特殊な型の構築 [hklm \software\microsoft \Visual Studio\\*\<Visual Studio version >*\FontAndColors\\`<Category>`]  
  
     *\<カテゴリ >*カテゴリのローカライズされていない名前を指定します。  
  
-   2 つの値を使用してレジストリを設定します。  
  
    |name|型|データ|説明|  
    |----------|----------|----------|-----------------|  
    |カテゴリ|REG_SZ|GUID|GUID は、カテゴリを識別するために作成します。|  
    |Package|REG_SZ|GUID|カテゴリをサポートする VSPackage サービスの GUID です。|  
  
 レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>の対応するカテゴリ。  
  
## <a name="to-create-or-identify-groups"></a>作成またはグループを識別するには  
  
-   カテゴリのレジストリ エントリの特殊な型の構築 [hklm \software\microsoft \Visual Studio\\*\<Visual Studio version >*\FontAndColors\\  *\<グループ >*]  
  
     *\<グループ >*グループのローカライズされていない名前を指定します。  
  
-   2 つの値を使用してレジストリを設定します。  
  
    |name|型|データ|説明|  
    |----------|----------|----------|-----------------|  
    |カテゴリ|REG_SZ|GUID|グループを識別する GUID が作成されます。|  
    |Package|REG_SZ|GUID|カテゴリをサポートするサービスの GUID です。|  
  
 レジストリで指定されたサービスの実装を提供する必要があります`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`対応するグループです。  
  
## <a name="to-implement-ide-support"></a>IDE のサポートを実装するには  
  
-   実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>、いずれかが返されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイスまたは`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`インターフェイスごとに IDE を**カテゴリ**またはグループの GUID を指定します。  
  
-   各**カテゴリ**をサポートし、VSPackage 実装の個別のインスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイスです。  
  
-   メソッドの実装を通じて<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>を使用して IDE を提供する必要があります。  
  
    -   リストの**項目を表示**で、**カテゴリ。**  
  
    -   ローカライズ可能な名前**項目を表示**です。  
  
    -   各メンバーの情報を表示**カテゴリ**です。  
  
    > [!NOTE]
    >  各**カテゴリ**少なくとも 1 つ含める必要があります**表示項目**です。  
  
-   IDE を使用して、`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`いくつかのカテゴリの共用体を定義するインターフェイスです。  
  
     その実装を使用して IDE を提供します。  
  
    -   一覧、**カテゴリ**特定のグループを構成します。  
  
    -   インスタンスへのアクセス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>それぞれをサポートする**カテゴリ**グループ内。  
  
    -   ローカライズ可能なグループの名前。  
  
-   IDE を更新しています。  
  
     IDE に関する情報をキャッシュする**フォントおよびカラー**設定します。 IDE の変更後にそのため、**フォントおよびカラー**構成では、キャッシュが最新であるかどうかを確認することをお勧めします。  
  
 キャッシュの更新は、操作には、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます。  
  
## <a name="to-handle-font-and-color-changes"></a>フォントと色を処理するために次のように変更します。  
 VSPackage を表示するテキストの色づけを正しくサポートするには、VSPackage をサポートする色付けサービスはを通じて行われますが、ユーザーによる変更に応答する必要があります、**フォントおよび色**プロパティ ページ。 VSPackage で。  
  
-   実装することによって IDE で生成されたイベントを処理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>インターフェイスです。  
  
     IDE は、次のユーザーの変更の適切なメソッドを呼び出して、**フォントおよび色**ページ。 たとえば、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>メソッドの場合は、新しいフォントを選択します。  
  
     - または -  
  
-   IDE の変更をポーリングしています。  
  
     これは、操作にはシステムに実装された<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスです。 永続化ストアのサポートについては、主には、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>のフォントと色の情報を取得するメソッドを使用できます**項目を表示**です。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)です。  
  
    > [!NOTE]
    >  確実にポーリングによって取得される結果が正しく使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得方法を呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [フォントとテキスト彩色の色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [ストアドのフォントおよび色の設定にアクセスします。](../extensibility/accessing-stored-font-and-color-settings.md)   
 [方法: 組み込みのフォントと配色へのアクセス](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [フォントと色の概要](../extensibility/font-and-color-overview.md)