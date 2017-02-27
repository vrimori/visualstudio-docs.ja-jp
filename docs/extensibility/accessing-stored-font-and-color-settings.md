---
title: "ストアドのフォントと色の設定にアクセスします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フォント、保存されている設定にアクセスします。"
  - "フォントおよびカラー コントロール [Visual Studio SDK] 持続性"
  - "色、保存されている設定にアクセスします。"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# ストアドのフォントと色の設定にアクセスします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 (IDE) がフォントを変更した設定を格納し、レジストリ内の色します。 使用することができます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> インターフェイスへのこれらの設定にアクセスします。  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>フォントと色の状態の永続化を開始するには  
 次のレジストリの場所でカテゴリ別のフォントと色の情報が格納されている: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< Visual Studio のバージョン>*\FontAndColors\\*\< CategoryGUID>*] ここで、 *\< CategoryGUID>* 、カテゴリの GUID です。  
  
 したがって、永続化を開始するには、VSPackage 必要があります。  
  
-   取得、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> を呼び出してインターフェイス `QueryService` グローバル サービス プロバイダーに対してです。  
  
     `QueryService` サービス ID の引数を使用して呼び出す必要があります `SID_SVsFontAndColorStorage` とのインターフェイス ID 引数 `IID_IVsFontAndColorStorage`します。  
  
-   使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> を引数としてカテゴリの GUID とモード フラグを使用して、永続化するカテゴリを開くメソッドです。  
  
     指定したモード、 `fFlags` 内の値から引数が構築された、 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 列挙します。 このモードを制御します。  
  
    -   経由でアクセスできる設定、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> インターフェイスです。  
  
    -   すべての設定またはのみユーザーを変更して、使用して取得できる、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> インターフェイスです。  
  
    -   ユーザー設定の変更を反映する方法です。  
  
    -   使用される色の値の形式です。  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>フォントと色の状態の永続化を使用するには  
 永続化するフォントと色が含まれます。  
  
-   IDE 設定をレジストリに格納されている設定と同期しています。  
  
-   レジストリの変更情報を伝達します。  
  
-   設定して、レジストリに格納されている設定を取得します。  
  
 IDE 設定で記憶域の設定を同期することはきわめて透過的です。 基になる IDE が自動的に更新された設定を書き込みます **表示項目** カテゴリのレジストリ エントリにします。  
  
 イベントが生成されることを VSPackage する必要があります複数 VSPackages には、特定のカテゴリが共有している場合とのメソッド、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> インターフェイスを使用してストアド レジストリ設定を変更します。  
  
 既定では、イベントの生成は無効です。 イベントの生成を有効にするを使用して、カテゴリを開く <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>します。 これが原因で、適切な呼び出しを IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage を実装するメソッドです。  
  
> [!NOTE]
>  によって変更、 **フォントおよびカラー** プロパティ ページの独立したイベントを生成する <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>します。 使用することができます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> インターフェイスのメソッドを呼び出す前にキャッシュされているフォントおよび色の設定の更新が必要かどうかを決定する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> クラスです。  
  
### <a name="storing-and-retrieving-information"></a>格納して、情報を取得します。  
 Vspackage の呼び出しを情報をユーザーが開いているカテゴリの名前付きの表示項目を変更できる構成を取得または、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> メソッドです。  
  
 フォントに関する情報を使用して特定のカテゴリを取得するための属性、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> メソッドです。  
  
> [!NOTE]
>   `fFlags` に渡される引数、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> そのカテゴリが開かれた場合は、メソッドの動作を定義する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> メソッドです。 既定では、これらのメソッドだけを返す情報 aboutdisplay itemsthat が変更されています。 ただし、カテゴリを使用して、開いている場合、 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 更新両方のフラグし、変更の表示項目はからアクセスできる <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>します。  
  
 既定では、のみ変更 **表示項目** 情報をレジストリに保持します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> フォントと色のすべての設定を取得するインターフェイスを使用できません。  
  
> [!NOTE]
>   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> メソッドは、変更に関する REGDB_E_KEYMISSING (0x80040152L) キューの使用は情報を取得するときを返す **表示項目**します。  
  
 すべての設定 **表示項目** 、特定の **カテゴリ** のメソッドを使用して取得できます、 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` インターフェイスです。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [カスタム カテゴリと [表示項目を実装します。](../extensibility/implementing-custom-categories-and-display-items.md)