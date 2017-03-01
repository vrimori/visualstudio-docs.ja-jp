---
title: "カスタム カテゴリと 表示項目を実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>カスタム カテゴリと 表示項目を実装します。
VSPackage には、フォントのコントロールとそのテキストの色を提供できる、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) のカスタム カテゴリとアイテムを表示します。  
  
 カスタム カテゴリとアイテムを表示、**フォントおよび色**プロパティ ページです。 開くには、**フォントおよび色**プロパティ ページで、**ツール** メニューのをクリックして**オプション**します。 展開**環境** をクリックし、**フォントおよび色**します。  
  
 Vspackage を実装する必要がありますこのメカニズムを使用する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスと関連付けられているインターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
 原則として、このメカニズムを使用して既存のすべてを変更する**項目を表示**と**カテゴリ**が含まれていること。 ただし、その指定しないでを変更する、**テキスト EditorCategory**またはその**項目を表示**します。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)します。  
  
 ユーザー設定を実装する**カテゴリ**または**項目を表示**VSPackage にする必要があります。  
  
-   作成するか、レジストリ内のカテゴリを特定します。  
  
     IDE の実装、**フォントおよび色**プロパティ ページでは、この情報を使用して、1 つのカテゴリをサポートするサービスのクエリを正常にします。  
  
-   作成またはレジストリに (省略可能) グループを識別します。  
  
     2 つまたは複数のカテゴリの和集合を表すグループを定義すると便利ですがある可能性があります。 グループが定義されている場合、IDE によって自動的にサブカテゴリをマージし、配布グループ内のアイテムを表示します。  
  
-   IDE のサポートを実装します。  
  
-   フォントと色の変更を処理します。  
  
 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)します。  
  
## <a name="to-create-or-identify-categories"></a>作成またはカテゴリを指定するには  
  
-   特殊な種類のレジストリ エントリの カテゴリの作成 [hklm \software\microsoft \Visual Studio\\*\<Visual Studio のバージョン >*\FontAndColors\\`<Category>`]  
  
     *\<カテゴリ >*カテゴリのローカライズされていない名前を指定します。  
  
-   2 つの値を使用してレジストリを設定します。  
  
    |名前|型|データ|説明|  
    |----------|----------|----------|-----------------|  
    |カテゴリ|REG_SZ|GUID|GUID は、カテゴリを識別するために作成されます。|  
    |パッケージ|REG_SZ|GUID|カテゴリをサポートする VSPackage サービスの GUID です。|  
  
 レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>の対応するカテゴリ</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>。  
  
## <a name="to-create-or-identify-groups"></a>グループを作成または識別するのには  
  
-   特殊な種類のレジストリ エントリの カテゴリの作成 [hklm \software\microsoft \Visual Studio\\*\<Visual Studio のバージョン >*\FontAndColors\\*\<グループ >*]  
  
     *\<グループ >*グループのローカライズされていない名前を指定します。  
  
-   2 つの値を使用してレジストリを設定します。  
  
    |名前|型|データ|説明|  
    |----------|----------|----------|-----------------|  
    |カテゴリ|REG_SZ|GUID|グループを識別する GUID が作成されます。|  
    |パッケージ|REG_SZ|GUID|カテゴリをサポートするサービスの GUID です。|  
  
 レジストリで指定されたサービスの実装を提供する必要があります`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`の対応するグループです。  
  
## <a name="to-implement-ide-support"></a>IDE のサポートを実装するには  
  
-   実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>、いずれかが返されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイスまたは`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`インターフェイスごとに IDE を**カテゴリ**または指定された GUID をグループ化します</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>。  
  
-   各**カテゴリ**をサポートし、VSPackage の個別のインスタンスを実装して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>。  
  
-   メソッドの実装を通じて<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>を使用して IDE を提供する必要があります:</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   リストの**項目を表示**で、**カテゴリ。**  
  
    -   ローカライズ可能な名前**項目を表示**します。  
  
    -   各メンバーの情報を表示**カテゴリ**します。  
  
    > [!NOTE]
    >  各**カテゴリ**少なくとも&1; つ含める必要があります**表示項目**します。  
  
-   IDE を使用して、`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`いくつかのカテゴリの和集合を定義するインターフェイスです。  
  
     その実装を使用して IDE を提供します。  
  
    -   一覧、**カテゴリ**特定のグループを構成します。  
  
    -   インスタンスへのアクセス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>それぞれをサポートする**カテゴリ**グループ内</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>。  
  
    -   ローカライズ可能なグループの名前です。  
  
-   IDE を更新するには。  
  
     IDE に関する情報をキャッシュする**フォントおよびカラー**設定します。 IDE の変更後にそのため、**フォントおよびカラー**構成では、キャッシュが最新であるかどうかを確認することをお勧めします。  
  
 キャッシュの更新を行う、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>。  
  
## <a name="to-handle-font-and-color-changes"></a>フォントと色を処理するには、次のように変更します。  
 VSPackage を表示するテキストの色付けを正しくサポートする、VSPackage をサポートする色付けサービスはを通じて行われたユーザーによる変更に応答する必要があります、**フォントおよび色**プロパティ ページです。 VSPackage では、、この検証を行います。  
  
-   IDE で生成されたイベントを実装することで処理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>。  
  
     IDE が次のユーザーの変更の適切なメソッドを呼び出して、**フォントおよび色**ページです。 たとえばの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>メソッドが新しいフォントが選択されている場合</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>。  
  
     または  
  
-   IDE の変更をポーリングしています。  
  
     これをシステムに実装された<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>。 主に、永続化のサポートでは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>のフォントと色の情報を取得するメソッドを使用できる**項目を表示**</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)します。  
  
    > [!NOTE]
    >  ポーリングによって取得される結果が正しくは、使用すると役立つ場合があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>の取得方法を呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを判断するインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [フォントとテキストの色づけの色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [ストアドのフォントと色の設定にアクセスします。](../extensibility/accessing-stored-font-and-color-settings.md)   
 [方法: ビルトインのフォントおよび画面の配色にアクセス](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [フォントと色の概要](../extensibility/font-and-color-overview.md)
