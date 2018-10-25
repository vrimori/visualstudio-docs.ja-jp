---
title: '方法: 組み込みのフォントおよび色スキームへのアクセス |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 295f6d26d086914bf75d5744ca47594dfefb6591
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911253"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>方法: 組み込みのフォントをアクセスし、ccheme の色
Visual Studio 統合開発環境 (IDE) では、エディター ウィンドウに関連付けられているフォントおよび色のスキームがあります。 このスキームを通じてアクセスできる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイス。

 組み込みのフォントとカラー スキームを使用して、VSPackage 必要があります。

- 既定のフォントおよび色のサービスを使用するカテゴリを定義します。

- 既定のフォントおよび色のサーバーで、カテゴリを登録します。

- 特定のウィンドウが使用して、組み込みの表示項目とカテゴリを使用することを IDE に案内、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer>インターフェイス。

  IDE では、ウィンドウのハンドルとして、結果として得られるカテゴリを使用します。 カテゴリの名前が表示されます、**設定の表示:** ドロップダウン ボックスで、**フォントおよび色**プロパティ ページ。

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>組み込みのフォントと色を使用してカテゴリを定義するには

1.  任意の GUID を作成します。

     この GUID は、カテゴリを一意に識別に使用されます。 このカテゴリには、IDE の既定のフォントおよび色の仕様が再利用されます。

    > [!NOTE]
    >  フォントおよび色のデータを取得するときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>またはその他のインターフェイスでは、Vspackage この GUID を使用して組み込みの情報を参照します。

2.  カテゴリの名前は、VSPackage のリソース内の文字列テーブルに追加する必要があります (*.rc*) ファイルを IDE に表示するときに、必要に応じてローカライズできるようにします。

     詳細については、次を参照してください。[を追加または削除する文字列](/cpp/windows/adding-or-deleting-a-string)します。

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>組み込みのフォントと色を使用してカテゴリを登録するには

1.  特殊な種類のカテゴリのレジストリ エントリの次の場所を作成します。

     *[Hklm \software\microsoft \Visual Studio\\\<Visual Studio のバージョン > \FontAndColors\\\<カテゴリ >*]

     *\<カテゴリ >* カテゴリのローカライズされていない名前を指定します。

2.  4 つの値をストックのフォントとカラー スキームを使用するレジストリを作成します。

    |名前|型|データ|説明|
    |----------|----------|----------|-----------------|
    |カテゴリ|REG_SZ|GUID|ストック フォントおよびカラー スキームを格納しているカテゴリを識別する任意の GUID。|
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> この GUID は、既定のフォントと色の構成を使用して、すべての Vspackage によって使用されます。|
    |NameID|REG_DWORD|ID|VSPackage のローカライズ可能なカテゴリ名のリソース ID。|
    |ToolWindowPackage|REG_SZ|GUID|VSPackage の実装の GUID、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイス。|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>システム指定のフォントと色の使用を開始します

1. インスタンスを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>ウィンドウの実装と初期化の一部としてインターフェイス。

2. 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>のインスタンスを取得するメソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer>現在に対応するインターフェイス<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インスタンス。

3. 呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>2 回クリックします。

   - 1 回呼び出す`VSEDITPROPID_ViewGeneral_ColorCategory`を引数として。

   - 1 回呼び出す`VSEDITPROPID_ViewGeneral_FontCategory`を引数として。

     これにより、設定し、ウィンドウのプロパティとして既定のフォントおよび色のサービスを公開します。

## <a name="example"></a>例
 次の例では、組み込みのフォントと色の使用を開始します。

```cpp
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

## <a name="see-also"></a>関連項目

- [フォントおよび色を使用して、](../extensibility/using-fonts-and-colors.md)
- [テキストの色づけのフォントと色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [アクセスには、フォントおよび色の設定が格納されています。](../extensibility/accessing-stored-font-and-color-settings.md)
- [フォントと色の概要](../extensibility/font-and-color-overview.md)