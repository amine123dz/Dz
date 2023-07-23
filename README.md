npm i && npm run start
import React from "react";

const ChatBubbleComp = (props) => {
  return <></>;
};

export default ChatBubbleComp;
import React from "react";

const ChatBubbleComponent = (props) => {
  const { uid, isLocal } = props;

  return <></>;
};

export default ChatBubbleComponent;
import React from "react";
import { useRender } from "customization-api";

const ChatBubbleComponent = (props) => {
  const { uid, isLocal } = props;

  // Get data from render app-state
  const { renderList } = useRender();

  // Fetch username using uid
  const displayName = renderList[uid].name;

  return <></>;
};

export default ChatBubbleComponent;
import { ChatBubble, useRender } from "customization-api";
import React from "react";

const ChatBubbleComponent = (props) => {
  const { uid, isLocal } = props;

  // Get data from render app-state
  const { renderList } = useRender();

  // Fetch username using uid
  const displayName = renderList[uid].name;

  return <ChatBubble {...props} />;
};

export default ChatBubbleComponent;
import { ChatBubble, useRender, $config } from "customization-api";
import React from "react";
import { View, Text, StyleSheet } from "react-native";

const ChatBubbleComponent = (props) => {
  const { uid, isLocal } = props;

  // Get data from render app-state
  const { renderList } = useRender();

  // Fetch username using uid
  const displayName = renderList[uid].name;

  const { container, containerLocal, containerRemote, username, usernameLocal, usernameRemote } = styles;

  return (
    <View style={[container, isLocal ? containerLocal : containerRemote]}>
      <View style={[username, isLocal ? usernameLocal : usernameRemote]}>
        <Text
          style={{ fontWeight: "bold", color: isLocal ? "black" : "white" }}
        >
          {displayName.slice(0, 1)}
        </Text>
      </View>
      <ChatBubble {...props} />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    display: "flex",
    flex: 1,
    alignItems: "flex-end",
  },
  containerLocal: {
    flexDirection: "row-reverse",
  },
  containerRemote: {
    flexDirection: "row",
  },
  username: {
    height: 32,
    width: 32,
    borderRadius: 16,
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
    marginBottom: "5px",
    backgroundColor: $config.PRIMARY_FONT_COLOR + "20",
  },
  usernameLocal: {
    marginLeft: -10,
    marginRight: 0,
  },
  usernameRemote: {
    marginLeft: 5,
    marginRight: -10,
  },
});

export default ChatBubbleComponent;
import { customize } from "customization-api";

import MyChatBubbleComponent from "./components/MyChatBubbleComponent";

const userCustomization = customize({
  components: {
    videoCall: {
      chat: {
        chatBubble: MyChatBubbleComponent,
      },
    },
  },
});

export default userCustomization;
import { customize } from "customization-api";

import MyChatBubbleComponent from "./components/MyChatBubbleComponent";

const userCustomization = customize({
  components: {
    videoCall: {
      chat: {
        chatBubble: MyChatBubbleComponent,
      },
    },
  },
});

export default userCustomization;
