---
title: "方法: ビルトインのフォントおよび画面の配色にアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フォント、組み込みへのアクセス"
  - "フォントおよびカラー コントロール [Visual Studio SDK] カテゴリ"
  - "組み込みスキームへのアクセスの色"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: ビルトインのフォントおよび画面の配色にアクセス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 統合開発環境 \(IDE\) では、エディター ウィンドウに関連付けられているフォントおよび色のスキームを持ちます。 このスキームを通じてアクセスできる、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> インターフェイスです。  
  
 組み込みのフォントと色のスキームを使用するのには、VSPackage 必要があります。  
  
-   既定のフォントおよび色のサービスで使用するカテゴリを定義します。  
  
-   既定のフォントおよび色のサーバーで、カテゴリを登録します。  
  
-   特定のウィンドウを使用して、組み込みの表示項目とカテゴリを使用することを IDE にアドバイス、 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` と `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` インターフェイスです。  
  
 IDE では、ウィンドウのハンドルとして結果のカテゴリを使用します。 カテゴリの名前に表示されます、 **設定の表示:** ドロップダウン ボックスで、 **フォントおよび色** \] プロパティ ページです。  
  
### 組み込みのフォントおよび色を使用してカテゴリを定義するには  
  
1.  任意の GUID を作成します。  
  
     この GUID を使用して、カテゴリを一意に識別**.**このカテゴリには、IDE の既定のフォントおよび色の仕様が再利用します。  
  
    > [!NOTE]
    >  フォントおよび色のデータを取得するときに、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> またはその他のインターフェイス vspackages にあるこの GUID を使用して組み込まれている情報を参照します。  
  
2.  カテゴリの名前は、IDE で表示されるときに、必要に応じてローカライズできるように、VSPackage のリソース \(.rc\) ファイル内の文字列テーブルに追加する必要があります。  
  
     詳細については、「[Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string)」を参照してください。  
  
### 組み込みのフォントおよび色を使用してカテゴリを登録するには  
  
1.  次の場所のレジストリ エントリのカテゴリの特殊な型を作成します。  
  
     \[Hklm \\software\\microsoft \\Visual Studio\\*\< Visual Studio のバージョン \>*\\FontAndColors\\*\< Category \>*\]  
  
     *\< category \>* カテゴリのローカライズされていない名前を指定します。  
  
2.  ストックのフォントおよび画面の配色を 4 つの値を使用するレジストリを設定します。  
  
    |名前|型|データ|説明|  
    |--------|-------|---------|--------|  
    |カテゴリ|REG\_SZ|GUID|ストックのフォントと色のスキームを含むカテゴリを識別する任意の GUID です。|  
    |パッケージ|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> この GUID は、既定のフォントと色の構成を使用するすべての VSPackages によって使用されます。|  
    |NameID|REG\_DWORD|ID|VSPackage でローカライズ可能なカテゴリの名前のリソース ID。|  
    |ToolWindowPackage|REG\_SZ|GUID|VSPackage の実装の GUID、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> インターフェイスです。|  
  
3.  
  
### システム標準のフォントと色の使用を開始するには  
  
1.  インスタンスを作成、 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` ウィンドウの実装と初期化の一部としてのインターフェイスです。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> のインスタンスを取得するメソッド、 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 現在に対応するインターフェイス <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> インスタンス。  
  
3.  呼び出す <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 2 回クリックします。  
  
    -   使用して 1 回呼び出す `VSEDITPROPID_ViewGeneral_ColorCategory`を引数として。  
  
    -   使用して 1 回呼び出す `VSEDITPROPID_ViewGeneral_FontCategory` を引数として。  
  
     これにより、設定し、ウィンドウのプロパティとして既定のフォントおよび色のサービスを公開します。  
  
## 使用例  
 次の例では、組み込みのフォントと色の使用を開始します。  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## 参照  
 [フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md)   
 [フォントとテキストの色づけの色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [ストアドのフォントと色の設定にアクセスします。](../extensibility/accessing-stored-font-and-color-settings.md)   
 [フォントと色の概要](../extensibility/font-and-color-overview.md)