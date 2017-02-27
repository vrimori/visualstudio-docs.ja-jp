---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS 列挙型"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) または [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) インターフェイスのさまざまな属性を記述します。  [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造体のメンバー。  
  
## 構文  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```c#  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## メンバー  
 DBG\_ATTRIB\_NONE  
 属性は表示されません。  
  
 DBG\_ATTRIB\_ALL  
 すべての属性が表示されます。  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 参照またはプロパティは子があることを示します。  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 このオブジェクトの ID が作成されたことを示します。  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 このオブジェクトの ID を作成できることを示します。  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 値は読み取り専用であることを示します。  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 値はエラーであることを示します。  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 評価が副作用を導入したことを示します。  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 このプロパティがオーバーロードのコンテナーであることを示します。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 `DEBUG_PROPERTY_INFO::bstrValue` の値がブール値であることを示します。  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 `DEBUG_PROPERTY_INFO::bstrValue` の値がブール型`TRUE` であることを示します。  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 `DEBUG_PROPERTY_INFO::bstrValue` の値が無効であることを示します。  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 `DEBUG_PROPERTY_INFO::bstrValue` の値が 「  *実行しない*  」であることを示します \(NAT\)。  \[NAT は 64 ビット Intel プロセッサで遅延段階的な例外を示すフラグの登録について説明します。  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 `DEBUG_PROPERTY_INFO::bstrValue` の値が自動配置されたことを示しています。  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 評価に指定されていることを示します。  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 `DEBUG_PROPERTY_INFO::bstrValue` の値が元の文字列で表現できることを示します。  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 このプロパティに関連付けられた 1 文字以上のカスタム ビューアーがあることを示します。  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 `public` も`private``protected` の種類のアクセスはなくオブジェクトが表示されます。  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 パブリック アクセスできるオブジェクトが表示されます。  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 プライベート アクセスできるオブジェクトが表示されます。  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 アクセスを保護してオブジェクトを示します。  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 最終的にアクセスできるオブジェクトが表示されます。  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 `DBG_ATTRIB_FLAGS` のアクセスの属性を抽出するマスク。  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 指定されたストレージ型がないことを示します。  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 グローバルなストレージを示します。  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 静的ストレージを示します。  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 登録のストレージを示します。  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 `DBG_ATTRIB_FLAGS` のストレージ属性を抽出するマスク。  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 型修飾子がないことを示します。  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 オブジェクトの型が仮想であることを示します。  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 オブジェクトの型が設定されていることを示します。  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 オブジェクトの型が同期されていることを示します。  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 オブジェクトの型が volatile であることを示します。  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 `DBG_ATTRIB_FLAGS` 型から属性を抽出するマスク。  
  
 DBG\_ATTRIB\_DATA  
 このオブジェクトはデータ フィールドであることを示します。  
  
 DBG\_ATTRIB\_METHOD  
 このオブジェクトはメソッドであることを示します。  
  
 DBG\_ATTRIB\_PROPERTY  
 このオブジェクトはプロパティであることを示します。  
  
 DBG\_ATTRIB\_CLASS  
 このオブジェクトはクラスであることを示します。  
  
 DBG\_ATTRIB\_BASECLASS  
 このオブジェクトは基本クラスであることを示します。  
  
 DBG\_ATTRIB\_INTERFACE  
 このオブジェクトがインターフェイスであることを示します。  
  
 DBG\_ATTRIB\_INNERCLASS  
 このオブジェクトが内部クラスであることを示します。  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 このオブジェクトは「 most\-derived であることを示します。  用語にはオブジェクトの実際の型参照のない型を 「  *」*  *最も* 。  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 `DBG_ATTRIB_MOSTDERIVED` によって `DBG_ATTRIB_DATA` マスクが表示されます。  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 オブジェクトに関連付けられている複数のカスタム ビューアーがあることを示します。  
  
## 解説  
  
> [!NOTE]
>  この列挙体の値はC\# のアセンブリで実際に定義されていません。  代わりにソース ファイルの定義をコピーする必要があります。  
  
 引数として渡された場合これらのフラグは [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) オブジェクトの子を使用するとたとえばフィルター処理することができます。  値はビットごと `OR` に組み合わせることがあります。  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` フラグは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] に [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスから [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) インターフェイスを取得しカスタム ビューアーの一覧の [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) を呼び出す示します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)