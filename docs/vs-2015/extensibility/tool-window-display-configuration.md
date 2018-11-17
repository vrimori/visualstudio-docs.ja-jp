---
title: ツール ウィンドウの表示の構成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c563888424ae4825f3e5b10fc0592029a29cb84b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736960"
---
# <a name="tool-window-display-configuration"></a>ツール ウィンドウの表示構成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage でツール ウィンドウ、既定の位置、サイズ、ドッキング スタイル、およびその他の可視性の情報を登録する場合は、省略可能な値で指定されます。 ツール ウィンドウの登録の詳細については、次を参照してください[ツールの Windows レジストリで。](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>ウィンドウの表示情報  
 ツール ウィンドウの基本的な表示の構成は、最大 6 個の省略可能な値に格納されます。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|名前|REG_SZ|「の短い名前をここに挿入」|ツール ウィンドウを説明する短い名前。 レジストリ内の参照にのみ使用します。|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|次の 4 つのコンマ区切りの値。 X1, Y1 はツール ウィンドウの左上隅の座標。 X2, Y2 は右下隅の座標。 すべての値は、画面座標でです。|  
|スタイル|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> 「リンク先」<br /><br /> 「タブ」<br /><br /> "AlwaysFloat"|最初に指定するキーワードは、ツール ウィンドウの状態を表示します。<br /><br /> "MDI"= MDI ウィンドウとドッキングします。<br /><br /> 「フローティング」浮動小数点を = です。<br /><br /> 「リンクされた」= (ウィンドウのエントリで指定された) 別のウィンドウにリンクされています。<br /><br /> 「タブ付き」= 別のツール ウィンドウと組み合わせます。<br /><br /> "AlwaysFloat"= ドッキングことはできません。<br /><br /> 詳細については、以下のコメント セクションを参照してください。|  
|[Window]|REG_SZ|*\<GUID &GT;*|これをツール ウィンドウのリンクやタブ付きウィンドウの GUID です。 GUID は、独自の windows のいずれかまたはで windows のいずれかに属している可能性があります、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE。|  
|[方向]|REG_SZ|"Left"<br /><br /> "Right"<br /><br /> "Top"<br /><br /> "Bottom"|以下のコメント セクションを参照してください。|  
|DontForceCreate|REG_DWORD|0 または 1|このエントリが存在し、その値が 0 でない場合、ウィンドウが読み込まれましたが、すぐに表示されます。|  
  
### <a name="comments"></a>コメント  
 印刷の向きのエントリは、そのタイトル バーをダブルクリックしたときにツール ウィンドウがドッキング位置を定義します。 ウィンドウのエントリで指定されたウィンドウに対する相対位置パスです。 スタイル エントリは、「リンクされた」に設定されている場合、向きエントリは、"Left"、"Right"、"Top"または"Bottom"にすることができます。 場合は、スタイルのエントリは、「タブ」、向きのエントリ「おくことができます」または"Right"をタブが追加されますを指定します。 スタイルのエントリが「フローティング」場合は、ツール ウィンドウは最初に寄せて配置します。 タイトル バーがダブルクリックされたとき向きとウィンドウのエントリを適用して、ウィンドウは、「タブ」スタイルを使用します。 スタイルのエントリが"AlwaysFloat"の場合は、ツール ウィンドウをドッキングことはできません。 スタイルのエントリが"MDI"の場合は、ツール ウィンドウは、MDI 領域にリンクされているし、ウィンドウのエントリは無視されます。  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>ツール ウィンドウの表示  
 オプションの可視性のサブキーの値では、ツール ウィンドウの可視性の設定によって決まります。 ウィンドウの可視性を必要とするコマンドの Guid を格納する値の名前が使用されます。 コマンドを実行すると、IDE は、ツール ウィンドウが作成され、表示されることを保証します。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|(既定)|REG_SZ|なし|空のままにします。|  
|*\<GUID &GT;*|REG_DWORD または REG_SZ|0 または説明する文字列。|任意。 エントリの名前は、可視性を必要とするコマンドの GUID である必要があります。 値は、情報の文字列だけを保持します。 通常、値は、`reg_dword`を 0 に設定します。|  
  
### <a name="example"></a>例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPackage の基本事項](../misc/vspackage-essentials.md)

