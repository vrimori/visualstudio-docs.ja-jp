---
title: レガシ API を使用してビューの設定の変更 |Microsoft Docs
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
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df84fa92cb0da8dd408b1cc8717628afa3d5ba19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730633"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>レガシ API を使用してビューの設定の変更
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ユーザーによってワード ラップ、選択余白、および仮想の領域などのコア エディター機能の設定を変更することができます、**オプション** ダイアログ ボックス。 ただし、これらの設定を変更することはもプログラムを使用します。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>レガシ API を使用して設定を変更します。  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイスが一連のテキスト エディターのプロパティを公開します。 テキスト ビューには、テキスト ビューの変更をプログラムで設定のグループを表すカテゴリ プロパティ (GUID_EditPropCategory_View_MasterSettings) にはが含まれています。 ビューの設定をこの方法で変更された後で変更できません、**オプション**リセットされるまで、ダイアログ ボックス。  
  
 コア エディターのインスタンスの表示設定を変更するための一般的なプロセスを次に示します。  
  
1.  呼び出す`QueryInterface`で、(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイス。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>の GUID_EditPropCategory_View_MasterSettings の値を指定して、メソッド、`rguidCategory`パラメーター。  
  
     これを行うにポインターを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイスでは、一連ビューの強制プロパティにはが含まれています。 このグループ内のすべての設定を完全に実行されます。 このグループで、設定がないかどうかで指定されたオプションに従います、**オプション** ダイアログ ボックスまたはユーザーのコマンド。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>で適切な設定値を指定して、メソッド、`idprop`パラメーター。  
  
     たとえば、ワード ラップを強制的に呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>VSEDITPROPID_ViewLangOpt_WordWrap の値を指定して`vt`の`idprop`パラメーター。 この呼び出しで`vt`VT_BOOL 型のバリアントと`vt.boolVal`は VARIANT_TRUE です。  
  
## <a name="resetting-changed-view-settings"></a>変更されたビューの設定をリセットします。  
 コア エディターのインスタンスの設定の変更された任意のビューをリセットするには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>メソッドの適切な設定値を指定し、`idprop`パラメーター。  
  
 たとえば、ワード ラップを自由にフロートを許可するのにはから削除するプロパティのカテゴリを呼び出して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>VSEDITPROPID_ViewLangOpt_WordWrap の値を指定して、`idprop`パラメーター。  
  
 コア エディターの設定が変更されたすべてを一度に削除するには、VSEDITPROPID_ViewComposite_AllCodeWindowDefaults の vt の値を指定、`idprop`パラメーター。 この呼び出しで vt は VT_BOOL 型のバリアントと vt.boolVal は VARIANT_TRUE です。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター内で](../extensibility/inside-the-core-editor.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [[オプション] ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)

