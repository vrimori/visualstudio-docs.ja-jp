---
title: ツール ウィンドウの表示の構成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 175e2005047312f6815e90c21c60ab831c036064
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tool-window-display-configuration"></a>ツール ウィンドウの表示の構成
VSPackage でツール ウィンドウ、既定の位置、サイズ、ドッキング スタイル、およびその他の可視性の情報を登録するときは、省略可能な値で指定されます。 ツール ウィンドウの登録の詳細については、次を参照してください[レジストリのツール ウィンドウ。](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>ウィンドウの表示情報  
 ツール ウィンドウの基本的なディスプレイの構成は、最大 6 つの省略可能な値に格納されます。  
  
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
|名前|REG_SZ|「短い名前をここに挿入」|ツール ウィンドウを説明する短い名前。 レジストリ内の参照でのみ使用されます。|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|次の 4 つのコンマ区切りの値。 X1, Y1 はツール ウィンドウの左上隅の座標。 X2, Y2 は右下隅の座標。 すべての値は、画面座標でです。|  
|スタイル|REG_SZ|"MDI"<br /><br /> 「フローティング」<br /><br /> 「リンク」<br /><br /> 「タブ付き」<br /><br /> "AlwaysFloat"|初期を指定するキーワードは、ツール ウィンドウの状態を表示します。<br /><br /> "MDI"= MDI ウィンドウをドッキングします。<br /><br /> 「フローティング」浮動小数点を = です。<br /><br /> 「リンク」= = (ウィンドウのエントリで指定された) 別のウィンドウでリンクします。<br /><br /> 「タブ付き」= 別のツール ウィンドウと組み合わせて使用します。<br /><br /> "AlwaysFloat"= ドッキングされることはできません。<br /><br /> 詳細については、以下のコメント セクションを参照してください。|  
|ウィンドウ|REG_SZ|*\<GUID &GT;*|ツール ウィンドウのリンクやタブ付きウィンドウの GUID です。 GUID が独自のウィンドウのいずれかまたはで windows のいずれかに属している可能性があります、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE です。|  
|[方向]|REG_SZ|"Left"<br /><br /> 「右」<br /><br /> "Top"<br /><br /> "Bottom"|以下のコメント セクションを参照してください。|  
|DontForceCreate|REG_DWORD|0 または 1|このエントリが存在し、その値が 0 でない場合、ウィンドウが読み込まれましたが、すぐに表示されます。|  
  
### <a name="comments"></a>コメント  
 印刷の向きエントリでは、タイトル バーをダブルクリックしたときに、ツール ウィンドウがドッキング位置を定義します。 ウィンドウのエントリで指定されたウィンドウの相対位置パスです。 スタイル エントリは、「リンクされた」に設定されている場合、印刷の向きのエントリは、"Left"、「右」、"Top"または"Bottom"に指定できます。 スタイル エントリは、「タブ付き」、印刷の向きエントリおくことができます""または"Right"と、タブを追加する場所を指定します。 スタイルのエントリが「フローティング」の場合、ツール ウィンドウは最初に寄せて配置します。 タイトル バーをダブルクリックしたとき、印刷の向きとウィンドウのエントリが適用され、ウィンドウが「タブ付き」スタイルを使用します。 スタイル エントリが"AlwaysFloat"の場合は、ツール ウィンドウがドッキングされることはできません。 スタイル エントリが"MDI"の場合は、ツール ウィンドウは、MDI 領域にリンクされているし、ウィンドウのエントリが無視されます。  
  
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
 オプションの可視性サブキーの値には、ツール ウィンドウの表示設定が決まります。 値の名前は、ウィンドウの可視性を必要とするコマンドの Guid の格納に使用されます。 場合に、コマンドを実行すると、IDE は、ツール ウィンドウが作成され、表示されることを保証します。  
  
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
|*\<GUID &GT;*|REG_DWORD または REG_SZ|0 または説明の文字列です。|任意。 エントリの名前は、可視性を必要とするコマンドの GUID にする必要があります。 値には、わかりやすい文字列だけを保持します。 通常、値は、`reg_dword`を 0 に設定します。|  
  
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
 [VSPackage](../extensibility/internals/vspackages.md)